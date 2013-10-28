---
layout: post
title: "Web Apps &amp; Code Retreats"
date: 2013-10-28 09:22
comments: true
categories: journey
---

Our latest project, finished last week, was [IdeaBox](http://tutorials.jumpstartlab.com/projects/idea_box.html). As mentioned in a previous post, we started building the project from a tutorial, without tests, and went from there. <!-- more --> I added unit tests before the weekend, and then started using Capybara for acceptance tests last. After watching the [RailsConf talk on BDD](http://www.youtube.com/watch?v=BG_DDUD4M9E), I realized I'd much rather work from the outside-in approach demonstrated in the talk.*

After building through IdeaBox on our own, we presented the projects on Thursday afternoon. It was great to see everybody's work, and see how far they got in the project, learn about their "a-ha!" moments, and also hear about pain points. It was great to see a project starting to turn out differently -- I'm sure as the course progresses, we will end up with vastly different projects than in the first third of the course.

On Friday, we all left the classroom and Galvanize to have an all-day code retreat. We made our way to the [RiNo](http://www.rivernorthart.com/) part of Denver and spent the day inside of [The Source](https://www.facebook.com/thesourcedenver), a rehabbed warehouse-turned-young-money-shopping-facility. (I'm probably totally wrong, but that's the best way I can describe it). We spent the day pairing in 30 minute time blocks, switching partners after every time block, and working on the same problem from scratch in a different way. In the morning, we worked through the [Beer Song](https://github.com/JumpstartLab/code_retreat/tree/master/beer) problem spec, and in the afternoon we worked through the [Robot](https://github.com/JumpstartLab/code_retreat/tree/master/robot) spec. Each was interesting in it's own way, and both tested fundamentals -- working with strings, or working with arrays and hashes. 

It was exciting to work with so many different classmates, and come up with so many different solutions, based on different contraints. I learned about how to build a program with no conditional statements (since `if` is not object oriented), learned about traversing through an array using modulo math, and various other amazing tidbits. I had a lot of fun, learned a bunch, and left at the end of the day completely exhausted, but mentally invigorated. I hope that I can continue to participate in code retreats beyond gSchool -- it seems like an amazing way to keep developers sharp and practice different pairing techniques.

I'm really enjoying being back in web territory. I have a foundational understanding some things already, so I can focus on testing the applications, using Ruby, and building things in a TDD (or BDD) fashion. I definitely like Sinatra, and that it's lightweight enough that you can choose your own design pattern, your own database ORM, and pretty much everything inbetween. In contrast, I started playing with Rails for the first time last week, and I'm not sure how I feel about how much work it does for the developer. I'm sure I'll change my mind once I know how to build everything from scratch really well and don't want to always do it myself, but for now I enjoy learning how to implement all of the pieces.

---

***Side note:***
* My reason for liking the idea of BDD comes from the various times I've been bitten by not having a way to test the entire experience from a user perspective. Our workload at my previous position was so high that often the developers would run through scenarios at a high level, test that things worked on their own machines, and ship the code to production. Often, many things went wrong in this process, sometimes after the client had already seen the problems themselves. We had started out with QA testers, but over time the people in the company that did QA on development projects were eventually reassigned to other things, leaving the developers without dedicated QA resources, and no time to do testing themselves. I would have loved to be able to do BDD back then, but then again, I'm just learning about it now! I think I might give this approach a shot in a future project at gSchool, just to see how it differs from starting with unit tests first.


