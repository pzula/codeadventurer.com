---
layout: post
title: "Build Your Own API Data Vaccum with Sinatra, Redis, and MongoDB"
date: 2014-06-23 20:57
comments: true
categories: tutorial sinatra api mongodb redis sidekiq
---

After setting up a SparkCore device (an internet-connected, Arduino-like device) to report the temperature and humidity in my greenhouse, I had one problem: persistance of the data. The SparkCore can transmit data via their SparkCloud API if you assign a variable for it in your Arduino code, and so I had a place where the data was constantly being transmitted. However, since the SparkCore itself has very limited memory capabilities, and since the only thing the SparkCloud itself does it provide a JSON-formatted API, I needed to figure out how to periodically ping the API and scoop up the data into a database.

This didn't seem like a job for the heft of Rails, so I started with Sinatra. My goals were to create something that others could reuse, improve upon, and deploy easily. Below I'll outline how to build your own API-slurping app from scratch. If you'd rather just grab the code and hack on it, you can find it on GitHub at <https://github.com/pzula/greenhouse-watchman>.The evolution of the project is evident through the [commit log](https://github.com/pzula/greenhouse-watchman/commits/master), so you can see how I started building up from a few simple files to a more organized solution.

In this walkthrough, I'll be showing you how I built a simple Sinatra app with Redis and MongoDB to suck out data from and API and store it in a database for use in a data visualization project.

<!-- more -->

## Figure out what data you are trying to store
For this project, I know that I have a few simple things that I want to store: temperature and humidity readings, along with the time of each reading. Each of these pieces of data have their own API endpoint that I can access in order to read the data. My endpoints look like this: `https://api.spark.io/v1/devices/myDeviceID/temperature?access_token=myAccessToken` and `https://api.spark.io/v1/devices/myDeviceID/humidity?access_token=myAccessToken` Explore your situation, and modify the instructions below to better suit your needs.

## Ruby version
I'm using Ruby 2.1.2 for this tutorial, and all of the latest versions on [RubyGems](http://rubygems.org) as of this writing for this walkthrough. You can find installation instructions for getting your machine set up with [this tutorial from JumpstartLab](http://tutorials.jumpstartlab.com/topics/environment/environment.html). Be sure to have Bundler installed (you can install it with `gem install bundler` once your Ruby environment is all set up).

## Start with a clean slate
Create a new folder for this project, as it will contain quite a few files by the end.

## Install MongoDB and Redis on your system
Assuming a Mac OSX system, using homebrew:
`brew install mongodb` and then follow the instructions output to the terminal to launch it.
`brew install redis`, and then follow the instructions output to the terminal to launch it.
Both will need to be running for this project.

## Set up your Gemfile with Sinatra, MongoDB, and Mongoid
First things first: You're going to need a few gems to get you off the ground running.
Create a `Gemfile` file, and add the following to it:

```ruby
source "https://rubygems.org"
ruby "2.1.2"

gem 'sinatra'

gem 'bson'
gem 'mongo'
gem 'mongoid'
```

MongoDB uses `bson`, which is short for Binary JSON for data representation. We'll also be using the Mongoid gem as our Object-Document-Mapper (ODM). You can think of it as an interface to the database that is similar to how ActiveRecord is used to interact with MySQL and PostgreSQL databases.

Run `bundle install` to get all of the gems and dependencies installed, and we'll be ready to get started.

Next we'll get our Mongoid configuration all set up. You'll need a file named `mongoid.yml`. This file will look like this to start with:

```ruby
development:
  sessions:
    default:
      database: greenhouse_watchman
      hosts:
        - localhost:27017
```

We'll create a simple file called `application.rb`. This file will look like this:

```ruby
require 'sinatra'
require 'mongoid'
require 'json'

get '/add-data' do
  Humididty.create(date: Time.now, reading: 46.8)
  Temperature.create(date: Time.now, reading: 87.2)
  'Great! You triggered fake data creation!'
end

get '/data.json' do
  content_type :json
  all_data = Temperature.all + Humidity.all
  all_data.to_json
end

class Humidity
  include Mongoid::Document

  field :date, type: Time
  field :reading, type: Float
end

class Temperature
  include Mongoid::Document

  field :date, type: Time
  field :reading, type: Float
end
```

Now, if you save that file, and load your app with the following command in the same folder as the file: `bundle exec ruby application.rb`, you will have started your server.
You can now visit `http://localhost:4567/add-data` to trigger the addition of one fake temperature reading and one fake humidity reading. If you then visit `http://localhost:4567/data.json`, you should see both readings output in a JSON format in your browser if everything is hooked up correctly. Awesome! We have our NoSQL data store hooked up properly, and we can write and read from it using Mongoid!

## Get the data with a background worker

Next, we're going to install Sidekiq as our background job processor. Sidekiq works with Redis to process your queue. We're going to be scheduling our background workers to go visit the API we want to suck data from, and allow the worker to process the response and store it in our database. By doing this in the background, none of our site visitors will have to wait for the data to be fetched from the API, and also we won't need to always have a browser window open to tell our server to go get the data periodically. It will all happen in the background, even as we sleep. (Well, as long as our server is running!)

We're also going to be using Faraday for our HTTP requests. Faraday gives us a simple interface to use HTTP requests in Ruby, so we'll add it as a dependency.

Add Sidekiq to your Gemfile like so: `gem 'sidekiq'`, and add Faraday with `gem 'faraday'` and then run `bundle install` to get your new gem and dependencies.
Now, at the top of you `application.rb` file, add these requirements:

```ruby
require 'sidekiq'
require 'redis'
require 'faraday'
```

Now we'll add a worker that will go get the data for us when it is invoked. In the bottom of the same file, you can add this new class:

```ruby
class APIWorker
  include Sidekiq::Worker

  $redis = Redis.new

  def perform(msg = "get_api_data")
    $redis.lpush(msg, store_data)
  end

  def store_data
    get_data("temperature", yourDeviceIDHere, yourAccessTokenHere)
    get_data("humidity", yourDeviceIDHere, yourAccessTokenHere)
  end

  def get_data(spark_var, device_id, access_token)
    request_url = "https://api.spark.io/v1/devices/" + device_id + "/" + spark_var  + "?access_token=" + access_token
    response = Faraday.get(request_url)

    parsed_response = JSON.parse(response.body)

    spark_var_to_model(spark_var).create(date: parsed_response['coreInfo']['last_heard'], reading: parsed_response['result'])
  end

  def spark_var_to_model(var)
    Module.const_get(var.capitalize)
  end
end
```

Now every time the `APIWorker` is called, `get_data` will get the data from our `request_url`, parse the response body as `JSON`, and insert the data appropriately from the JSON hash to our database. `spark_var_to_model` capitalizes our `spark_var` and creates the appropiate syntax to call our respective model, whether it is `Temperature` or `Humidity`.

Now, we'll need something to trigger our worker. Let's add another route to the `application.rb` file:

```ruby
get '/work' do
  SparkcoreWorker.perform_async
end
```
In a new terminal window, make sure to start up Sidekiq with this command: `bundle exec sidekiq -r ./application.rb`

If we start our server up again with `ruby application.rb` in a new terminal window, and visit our new route at `http://localhost:4567/work`, it will trigger our background job. How do we know if it worked? If we provided the correct `device_id` and `access_token` in the `perform` method above, it should have done it's job. We should see new data at `http://localhost:4567/data.json`, along with the dummy data we created previously.

If you're not sure your background jobs are working, you can look at the Sidekiq web interface. We're going to add a `Rake` task to allow you to start the Sidekiq GUI easily. Here you'll be able to see if background jobs have failed or have been processed. Create a new file with the filename: `Rakefile`, and add the following to it:

```ruby
task :monitor do
  require 'sidekiq/web'
  app = Sidekiq::Web
  app.set :environment, :production
  app.set :bind, '0.0.0.0'
  app.set :port, 9494
  app.run!
end
```

After you save it, you can run `bundle exec rake monitor` and visit the URL at `http://localhost:9494/sidekiq` to monitor the jobs. If any have failed and need to be retried, you can restart the failed job from here.

## Schedule the jobs

Now that we have our background job hooked up, there's one thing missing: it's being triggered by us manually visiting a route on our site. This isn't very efficient for data collection, so instead we're going to have to schedule our background job to run periodically on it's own. For that, we'll use the `Clockwork` gem.

In your Gemfile, add `gem 'clockwork'`, and run `bundle install` to get your new gem and dependencies.
Then, add another require statement in `application.rb` like so: `require 'clockwork'`

Then, at the bottom of the file, add this code to set up Clockwork:

```ruby
module Clockwork
  handler do |job|
    puts "Running #{job}"
  end

  every(2.minutes, 'apiworker.job') { APIWorker.perform_async }
end
```

After you save the file, you can start a third terminal window and get Clockwork running by executing: `clockwork application.rb`. If everything went well, you'll be getting new data pulled down from the API every 2 minutes, and stored into your database!

In the next blog post, I'll be showing you how to deploy this simple app to Heroku. If you have any questions, let me know [@pzula](http://www.twitter.com/pzula) on Twitter!
