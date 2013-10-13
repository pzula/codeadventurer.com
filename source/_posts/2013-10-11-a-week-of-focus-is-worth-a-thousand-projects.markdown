---
layout: post
title: "A week of focus is worth a thousand projects"
date: 2013-10-11 09:01
comments: true
categories: journey
---

This past week at gSchool, we broke out into groups based on how comfortable we felt with the projects we had done and the techniques and methods used in them. <!-- more --> We had an emerging group, a progress group, and an advanced group. In these groups, we would focus on taking what we knew, building on it, and pushing ourselves past our comfort levels.

I felt like I could get some benefit out of the exercises the emerging group has been working on (like locking in various ways of using hashes, arrays, and enumerators), but I also had a feeling that I might have a good enough grasp on those things that I could push myself in a different way. Instead, I chose to join in with Jeff's group, the progress group, to take a fresh look at our first paired project from a few weeks back, [EventReporter](http://tutorials.jumpstartlab.com/projects/event_reporter.html). 

The first time around this project, I had been tackling it from the provided test routes, one item at the time. I also had chosen not to work closely with my pair, because he had completed the assignment several times before and was beyond my level in terms of understanding how to do it, and I had wanted to learn how to go about it myself instead of watching someone code things I did not understand. If I had actually paired with him, I probably would have had the project completed, but I'm not sure if I would have learned as much. So originally, my EventReporter was not complete, nor very pretty.

It was great to step through the thought process with Jeff this week. He helped us understand how to break down the problem, how to start with an MVP, how to create test doubles (or stubs) so that our tests were independent of each other (in the case of unit tests), and to build small pieces of a project and get one piece working at a time using test-driven development. He also helped us understand when to use text fixtures, and when to use hard-coded data in tests. 

Throughout the week, we tacked a method or two a day, writing the tests, talking through the process, and slowly chipping away at the requirements. We started with a much better separation of concerns than the first time around (when many of us had everything in one giant method, in one giant file). It felt great to bring in all of our pieces yesterday, and write one controller that brought it all to life as a command line interface. After a little debugging, many of us had an EventReporter that worked, in half of the time with twice the quality of the first round.

Although I'm not yet a master of creating beautiful, small, concise methods, and knowing when to use `send` instead of an `if` statement, I have a great example with commit messages at every step to reference when I need to dig in and remember how we did things. 

It was great to work with a group at my same level of understanding for the week, and not be derailed by questions that are either to basic or too advanced for our current skillset. I'm not sure if I'd want the entire 24 weeks to work this way, but I do think that pairing with someone of a similar skill level is helpful. I have found that when I have been paired with someone who has been programming in Ruby for longer than the course, that they often do not explain their thought process and just forge ahead to get done with things, instead of hanging back to bring the person with less experience up to their level. I believe the true purpose of pairing is to slow down, explain your thought process, and pair through a problem together. If more advanced students were willing to do this without taking control of a project, I'd be happy to be paired with them. Otherwise, I'd rather stay with someone who is at the same level of understanding as me.

After this week of focus, which has helped me immensely in terms of understanding how to do things the right way (moreso than working independently on projects without much instruction) I'm excited that we're digging into web applications next week. Although I've built small web systems in PHP before, I know I have a lot to learn and am eager to get on the right path.

(**Title disclaimer**: *Ok, so perhaps more like worth two projects)

