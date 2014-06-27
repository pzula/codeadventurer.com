---
layout: post
title: "Beautiful, Dynamic Database Seeding Scripts"
date: 2014-02-01 18:54
comments: true
categories: rails
---

In our current Rails project, my team is building [FreshFinder](http://github.com/freshfinder), a community-edited Farmer's Market finder, with reviews. The main data we are using in our application, prior to user contributions, is data that we are pulling from [Data.gov](http://data.gov)'s Excel spreadsheet of USDA Farmer's Market Data. <!-- more -->A spreadsheet?? Yes. A spreadsheet. Because although they have a publicly-accessible API for the data, there are only two possible calls to this API, both of which do not contain all of the information otherwise contained in the Excel file.

Armed with the `CSV` Ruby library, some regex, some string splitting, and gsubbing, my team and I have been normalizing the data from the spreadsheet to build out a publically-accessible, RESTful API for our application's frontend to consume. While building it out, it makes sense to seed the database with real data from the spreadsheet, so I've been learning a lot about building beautiful, dynamic seed scripts for Rails.

The first thing to consider is that although when you run `rake db:seed`, you're calling upon the `/db/seed.rb` file in Rails, you aren't constrained to just using this file. In my seed file, I `require` the files which contain the classes and methods I need access to, like so:

```ruby
require './db/seeds/market_seeder'
require './db/seeds/product_seeder'

ProductSeeder.seed
MarketSeeder.seed(100)

```

As you can see in the code above, I then call the `seed` method on both the `ProductSeeder` and the `MarketSeeder` classes. But before I ever even got to the point of calling these two methods in my `seeds.rb`, I wrote some tests, and I recommend you do the same.

It's important to remember that seed files are just POR, Plain Old Ruby, and that testing them is just like testing any other Ruby code that you produce. In my `spec` folder, I created a subfolder called `seeds` and built out the [`market_seeder_spec.rb`](https://github.com/FreshFinder/to-the-market-api/blob/master/spec/seeds/market_seeder_spec.rb) file to test parsing the CSV file and to expect changes to the database upon running it.

When we talked about what we wanted our seeder to do, we had two things that were important to us: the first was that we could dynamically control how many items got seeded into the database. This was important because we didn't want to be building and testing our mapping and search functionality with the full 8,200 farmer's markets records during the first week of development. The second thing that was important to us was getting feedback during the seeding process, which usually means outputting to the screen a piece of information for each object seeded with a `puts` statement. Each of these things presented a new way of thinking about seeding data for us.

To create a dynamic seeding process from our parsed CSV file, we accept an optional parameter in our `seed` method that takes a number and injects it into a range that gets run on the collection that builds each market, like so:

```ruby
def self.seed(number = nil})
  data = MarketSeeder.parse_file('./db/seeds/source/2013_farmers_markets.csv')
  if number
    data.to_a[0...number].collect {|line| build_markets(line)}
  else
    data.collect {|line| build_markets(line)}
  end
end
```

The next piece of functionality, outputting the name of each market as each market was built with the `build_markets` method, was as simple as using a `puts` statement. However, the `puts` would output to the string even when a test was running, which quickly cluttered up test feedback. Thankfully, earlier in the week Katrina Owen had shown me a really neat concept I hadn't thought about before -- that you could change what `puts` is being executed on, and in turn, change where the string gets captured.

The way this is done is to define your output parameter, and set the default to `STDOUT`, like so:

```ruby
def self.seed(number = nil, out = STDOUT)
  data = MarketSeeder.parse_file('./db/seeds/source/2013_farmers_markets.csv')
  if number
    data.to_a[0...number].collect {|line| build_markets(line, out)}
  else
    data.collect {|line| build_markets(line, out)}
  end
end

def self.build_markets(line, out)
 m = Market.create!(:fmid => line[:fmid], :name => line[:marketname])
 out.puts line[:marketname]
end
```

You may be thinking, ok, so you're telling `puts` to run as a method on `STDOUT`, that's no different than it's default functionality. True. So in your test suite, you're going to require `StringIO`, like so:

```ruby
require 'stringio'

describe "Seeding a market" do
  before :each do
    @out = StringIO.new
  end

  it "changes the count on the Market database when seeded" do
    expect(Market.count).to eq 0
    expect { MarketSeeder.seed(2, @out) }.to change{Market.count}.by 2
  end
end

```

By piping `puts` to `StringIO`, you are capturing the feedback instead of outputting it to the string during testing, and thus relieved of the noise while running your specs.

After building our seed scripts for the first time using this method, I've had a much better experience than when I used to shovel everything straight into the `db/seeds.rb` file. My code is easier to read, shorter, and has a better seperation of concerns. I encourage you to give it a try, and let me know any other tricks to creating great seeds scripts!
