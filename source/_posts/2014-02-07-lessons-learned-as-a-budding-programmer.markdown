---
layout: post
title: "Lessons Learned as a Budding Programmer"
date: 2014-02-07 10:12
comments: true
categories: journey
---

## A little background

I wasn't new to computers five months ago when I started gSchool, a 6-month intensive & immersive course in learning Ruby and Ruby on Rails, but I might as well had been.

I had spent the previous six years as a web designer who had a knack for getting things to work right. I had set up VPS servers, built up content management systems, and even began building lead generation systems from scratch in PHP with MySQL backends. I had heard acronyms like OO and MVC, but really didn't know how to program in an object-oriented way, or why models, views, and controllers even mattered. I came to gSchool thinking I would naturally be a top student, as I had been in other courses and programs. I quickly realized this wasn't the case, but it took me some time to come to terms with that. Looking back on the last five months I think I know why, and hope to be able to help others learning how to program understand what is happening if they come across similar frustrations.

<!-- more -->

## A different way of thinking

If you aren't coming from a background like engineering or law, it may be that you aren't used to thinking in a way that is conducive to writing computer programs. A quick check to see if you might be naturally inclined to breaking down a problem into it's smallest logical parts is to pull out a [LSAT logic game](http://www.griffonprep.com/logicgame.html) and spend some time trying to figure it out. Did you get the right answers? Then you might not have the same struggles I had. Throughout grade school, whenever I saw one of these word problems, I shuddered and usually froze. I never got the right answer. It wasn't until my interview with Katrina Owen to join gSchool that I had finally understood how to solve these problems. I had always tried to solve these problems by keeping all of the information in my head without writing anything down or drawing a chart. Suddenly, with this hint at not trying to keep all the information in my head, I started to make some progress.

The first few weeks of the course, we spent at least 30 minutes every morning working on LSAT logic games, and every day I noticed that it took less and less time to get to the correct answers, now that I had an idea of how to break down my thoughts on paper. I didn't notice this at the time, but now that I've been programming non-stop for five months, I find that breaking out a pen and paper when a problem gets tough helps me visualize and articulate the problem so that I better understand it. Which leads me to one of the biggest take-a-ways from the last five months:

## You can't solve a problem that you don't understand.

Programming is so much more than just memorizing syntax and what the standard library gives you for free. It's about using those tools in a way that is effective. When I started gSchool, I didn't understand the Ruby syntax or the problems that we were trying to solve. Looking back, I know that I spent much more time worrying about not understanding the standard library than worrying about not understanding the problem. In my first course assessment, I was told that I had a much better understanding of Ruby than the evaluator had expected, but that my "algorithmic thinking" was weak. This was so very true. After that assessment, I started to shift the weight of my focus on solving smaller problems more frequently. I worked on features from top to bottom in our web-based projects using Capybara to build the feature tests. I paired with classmates and tried to talk through my thought process.

## Pairing is better than "rubber-ducking" for beginners

I heard about "rubber duck debugging" early in the course, which comes from the famous book, ["The Pragmatic Programmer"](http://pragprog.com/the-pragmatic-programmer), and suggests that a developer carry around a rubber duck and attempt to explain the problem to the duck. Usually, in the course of trying to explain the problem, the developer will better understand the problem herself and solve the issue without having to reach out to co-workers. Although this method is helpful now that I'm comfortable with Ruby, (without a real rubber duck...)  at the start of the course I found it was not as helpful as pairing. When faced with a tough problem early into the program, pairing with another student would lead to solving the problem faster, as well as gaining a better understanding of why the solution worked. This hasn't changed, as our projects become increasingly complex and the sheer number of things to be thinking about has grown exponentially, but now I find myself "rubber-ducking" my way through harder bugs without having to break the flow of my team's progress.

## Daily practice is the fastest way to improve

I knew that I needed to focus on learning how to build software in an intense environment, which I why I chose to come to a six month immersive course. But regardless of the situation, I do believe firmly that the best way to improve at programming -- whether or not you are a beginner -- is daily practice. Even if the daily practice is only an hour a day, if that time is focused, the daily habit is a great recipe for success. During the course, we have had a few interruptions in our schedule -- mainly holidays and a few weather events -- and I found that the best way to stay engaged and "in the game" was to program even during the interruptions in the course. A great tool for daily practice of syntax, style, problem-solving and test-driven development is [exercism.io](http://exercism.io), built by Katrina Owen. After we graduated from pen-and-paper LSAT problem-solving early in the course, we moved into warming up daily solving problems on exercism, which has been an amazing help.

## Reference the docs. A lot!

The documentation of the Ruby API may not be the best for beginners, but it's also open source. One of the best tools I have found for referencing documentation (even without an internet connection), is [Dash](https://itunes.apple.com/us/app/dash-docs-snippets/id458034879?mt=12). It's worth the $20 for the amount of time you'll save not going down a Google rabbit hole. Even if you're a seasoned programmer, it's a great tool. You can even find various [editor plugins](https://github.com/rizzatti/dash.vim) for even faster API reference straight from your codebase.

## The learning never stops, so don't give up!

I remember wanting to know all the things, all at once, at the start of gSchool. It was frustrating, and worse, it was unattainable. Our field is constantly changing, which means we'll never get bored. It also means that it's impossible to know everything. The beauty of being immersed in learning for six months is that we got a lot of exposure to different problems and different methods of solving them. Does this mean that any of us can walk away and sit down and build an entire complex web application without referencing any documentation? No. The reality is that all programmers reference the docs, and knowing what problem you are trying to solve will be infinitely more beneficial than memorizing the entire standard library. Work on learning how to break down complex problems, and the knowledge of the API will come.
