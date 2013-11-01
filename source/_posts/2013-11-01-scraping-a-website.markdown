---
layout: post
title: "Scraping a Website, Building a CMS"
date: 2013-11-01 09:12
comments: true
categories: journey
---

This week, we started a quick-turnaround project in Sinatra called [Clone Wars](http://tutorials.jumpstartlab.com/projects/clone_wars.html). Our challenge was to pick one of five local businesses, build a CMS for their existing types of content, and then scrape their existing website into our database -- all in three days. <!-- more -->

On Monday, before the project started, we took a little time to research web scrapers as a class. Afterwards, we did a short [tutorial](http://tutorials.jumpstartlab.com/topics/mechanize.html) with the [Mechanize](https://github.com/sparklemotion/mechanize) and [Nokogiri](https://github.com/sparklemotion/nokogiri) gems, and started scraping different websites.

We were assigned our teams in the afternoon, and got to planning out our project. We got up to speed on what local business we wanted to choose (we went for the [Bike Depot](http://thebikedepot.org/)), and started sketching out what the different types of content might look like. We set up our hours of availability as a team, and decided that we wanted to approach the entire project from an acceptance-test-first approach. It was our first time trying it, but we were all very interested in learning how to do it.

We then sat down with Elaine from [Pivotal Labs](http://pivotallabs.com/) (and prior gSchool student) to talk about user stories, acceptance tests, and [PivotalTracker](http://www.pivotaltracker.com/). She gave us a lot of good insight on how to use the tool, and soon we started crafting our user stories for the project.

Once we got to the point where we felt we had flushed out the project requirements from a user story perspective, we started digging in. We set up our Sinatra app, and began by writing our first Capybara user test. We ran that first test… and it passed. That didn't make any sense -- we had not set up any routes for the route that we had requested, and certainly did not have any views to display the content that the test requested! 

This problem tripped us up for over an hour, when we discovered that in our Gemfile we had declared a test group, but we had not yet set our environment variables in our acceptance test. We also later discovered that looking for content as the first piece of an acceptance test is too many steps into the process -- the first step would be to verify the response code. Finally on our way to a true failing test, we moved to the first piece of the error, and started working our way through the controller, the models, and the views. It was exciting to go through the process and actually successfully go from dummy data to a real database with real data in the matter of a few hours, and then repeat the process over and over again throughout the process.

From my perspective, our team worked incredibly well together. When one of us would get stuck, we'd stop and explain what was happening, and why. We all paired (side note: what is the three-person equivalent of pairing? Triading?) throughout the length of the project, since we  had a small enough project that it was likely we might end up with merge conflicts otherwise.

Although we did not completely finish building the CMS in three days, we learned a lot about scraping, dynamic routing, serializing data into databases, and setting up different rack test groups. We had an awesome time trying the acceptace-test-first approach, and stuck together as a group to work through tough problems. 

The differences between working in a two person versus a three person group weren't too obvious, since our project was so compact. I can definitely see where a four person group might split into two pairs that rotate, but with three people at different levels in the program, and with a small spec and a short timeframe, it seemed more appropriate to stick together and learn together.

If we had another week to work on Clone Wars, we'd likely get our authorization working correctly, and work on integrating more functionality into the CMS -- including the addition of news items, products for sale, and a volunteer database. 

Overall, I was extremely satisfied with where we got with our project because I felt that we built it well, communicated with each other clearly, and have a solid foundation to build upon when we choose to revisit the project.

To see the project in action, you can visit George's [GitHub repository](https://github.com/Egogre/CloneWarz), clone the project, run `bundle`, then run `rackup` in your terminal, and visit your localhost for a peek at the project. At localhost/admin, you can view our CMS functionality. Make sure to take a look at our test suite, and run the tests by running the `rake` command in your terminal. Then marvel at the beautiful rainbow of passing tests!

