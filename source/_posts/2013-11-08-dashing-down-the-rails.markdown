---
layout: post
title: "Dashing Down the Rails"
date: 2013-11-08 10:13
comments: true
categories: journey
---

It's amazing to look back on my time here at gSchool and realize that at this point in time, if I were in a shorter bootcamp program, I'd be graduating today. <!-- more --> Instead, I'm midway through my first Rails project, and learning about all of the features that Rails implements for me through a well-thought-out Ruby backend. When I want to write my own validators or database searches, I start down that journey, but then quickly realize that Rails has already taken care of it for me and that I just need to find the right method in the documentation. 

I can imagine what a contrast this is for people who learn as little Ruby as possible in order to get by using all the magic that Rails provides. I think that if I didn't know about the internals of how it worked, I would likely end up in the same boat as when I was hacking things together in Drupal. I have often heard that it is best to know Ruby before working with Rails, and now having experience with both Ruby, and Sinatra, I can see the differences between what Rails provides, and what the language itself does for me, which I think is very important for anyone using any framework.

Our current project is called [Dinner Dash](http://tutorials.jumpstartlab.com/projects/dinner_dash.html), and the task at hand is to build an online ordering system for a restaurant. My group has been working with MiniTest, RackTest & Capybara to use a BDD-style approach to the project, and we have also been using PivotalTracker to track our progress, combined with [git flow](http://nvie.com/posts/a-successful-git-branching-model/) to keep ourselves organized. My mentor works for PivotalLabs, and was very helpful in giving me a few more tips on how to use PivotalTracker to map through our user stories and scheduling our work and expectations. 

At the beginning of this project, I was having a hard time mapping my prior knowledge of SQL queries and database relationships to ActiveRecord, but now I have a better grasp on it thanks to two sessions with two different people that helped me understand what was happening. My mentor, Brian Rose from PivotalLabs, helped me understand the entity relationship diagram of our current application by installing the `rails-erd` gem into our project and generating a PDF of our relationships for me. This was helpful to see, and his explanations helped immensely. I also sat with Jorge and we drew a few diagrams with carefully placed labels to map out a new many-to-many relationship I was creating, and now I think I have a good hold on the whole `belongs_to`, `has_many`, `is_one_of` structure. 

I think that besides structuring models, views, and controllers well and understanding ActiveRecord, knowing all of the work that Rails can do might take a little time to learn and master -- but overall I'm enjoying working with it. My goals for this project are to get my feet wet with Rails, and start to understand where it can lift some of the burden of common tasks when building applications.

