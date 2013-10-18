---
layout: post
title: "Back to the land of HTTP requests"
date: 2013-10-18 08:58
comments: true
categories: journey
---

This week, we started using Sinatra to build a web application. At the start of the week, we built [WebGuesser](http://tutorials.jumpstartlab.com/projects/web_guesser.html), a random-number guessing site <!--more -->that allows for a user to guess the number, and gives feedback on how close they are. [My version](http://agile-peak-6795.herokuapp.com/) has a few bugs. For instance, if two people are accessing the site at the same time and playing, each person's guess counts towards the total, so you may only guess once or twice and be presented with a "Too many guesses" message. This can easily be solved with session cookies, but I haven't gotten around to refactoring yet. I'm sure I'll get a chance to come back and make that short project better.

We also started building [IdeaBox](http://tutorials.jumpstartlab.com/projects/idea_box.html), a place for someone to jot down ideas and store them. Originally, I just worked through the tutorial to have an understanding of the application, and then I implemented a few changes before writing tests. It was hard to work through the tutorial to understand what was happening and try to write tests at the same time, but now that I have gone back and written tests for the application, I am much more comfortable with moving forward with implementing the extensions. 

I actually feel that writing the tests gave me a better understanding of each piece of the application. I definitely felt the pain of not having tests when I had decided to change how IDs are generated and add them to the YAML database, without any tests to help me spot where things were breaking. I'm still shaky on the best ways to test web applications from the acceptance-test level, but I've got five more months to nail that piece!

What I like about this project is that we are working at our own pace. Some people will have amazing full-blown web apps with design, users, SMS capability, etc. at the end of this, others will have gone through the basic implementation, and everyone will have a better understanding of how web applications work. It's also been great to be in groups of four because we are all at different stages of the project, and can ask for help in specific places, instead of being dragged along by a stronger pair.

Next week, we're going to have our first assessment. I think we'll be paired with one of our instructors for the length of the assessment, and will have to build a program while being observed. This sounds a little intimidating, but the instructors are also there to provide feedback on our thought process and implementation, which I think is one of the coolest opportunities in the program. I think I'll be overall in a good place during the assessment, and I'm very eager to find out what I need to spend more time learning and understanding.