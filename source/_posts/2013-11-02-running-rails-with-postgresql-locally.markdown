---
layout: post
title: "Running Rails with PostgreSQL locally"
date: 2013-11-02 13:18
comments: true
categories: rails
---
I had a few issues installing Rails for the first time with PostgreSQL locally, and since the problems I was having as a newbie in both were not well-documented on the internet, I thought I'd post a rundown of what happened and how I fixed it. <!-- more -->

### Installing pgsql with home-brew

This topic has been covered exhaustively on the web, but the way I did it was to run:

```
$ brew update
$ brew install postgresql
```
Then, I followed the rest of the directions in the terminal to finish my install, and to install the pg gem.

***Big thing of note:*** If you are not sure you followed all the directions, and you're getting crazy errors, and you've already closed your terminal, all is not lost!

You can run `brew info postgresql` to see the instructions again and double check.


### Fixing your broken PG Connection in Rails

I decided to start my first rails project with pgsql, because I wanted to give it a try and after using sqlite3 a few times already, I was ready to graduate to something I could actually deploy on Heroku.

So I created my brand-new rails app by running this command in my terminal:

`rails new blogger -d postgresql`

Everything looked gravy, until I loaded up <http://localhost:3000> and got the big red Rails error with something I did not understand:

`PG::ConnectionBad (FATAL:  role "blogger" does not exist
):`

So I found that after doing that, I did some research and found that I needed to run the rake task to actually set up the databases. That's fine by me! So I ran this in my terminal:
`rake db:create:all`


Then, my terminal blew up and the error I would get would be: 
`FATAL:  role "blogger" does not exist`

Not knowing much about this, I spent some time searching and found out that I needed to create a new user named the same thing as the user in my `database.yml` file in the Rails app. Mine happens to be `blogger`, so I then went into my terminal and ran the following command:
`createuser -s -r blogger`

Then, I ran this command again, this time successfully: `rake db:create:all`

After doing this, and restarting my Rails server, I went back to <http://localhost:3000> and I was happily riding the Rails!