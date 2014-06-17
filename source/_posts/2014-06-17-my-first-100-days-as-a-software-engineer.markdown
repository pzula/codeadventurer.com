---
layout: post
title: "My First 100 Days as a Software Engineer"
date: 2014-06-17 07:58
comments: true
categories: journey
---

Today marks 100 days* since my first day as a software engineer at Hireology, and it's been an amazing experience.

A week before I officially became a software engineer, I packed up my apartment in Denver, shipped some bigger things home, packed the rest of my life in a suitcase and hopped back on a plane to Akron, Ohio.

I had done it -- I had learned as much as I could in the six months that I attended gSchool with my fellow classmates, and leveled up my game in building things on the web. I learned test-driven development, service oriented architecture, modular design and so many more things. And now, I had a week to reorganize my life, and start my job as a remote engineer on a product team.

<!-- more -->

I was excited, and I was nervous. I had seen parts of the code base during my interview process, and I had heard some of the other engineers talk about things I hadn't touched yet, like cucumber, mocking and stubbing, and services that encapsulated domain logic away from your models. Would I be able to catch on and hit the ground running? Or was I going to weigh down this small team of five?

I was very fortunate to have a friend and mentor already on the team. Matt, my mentor from my gSchool days, had been at Hireology since the fall. He was my onboarding buddy during my first week, and he helped me get my machine configured with our tools and codebase, got all of my various accounts set up, and got me familiar with the workflow. Margot, our product manager, already had a list of cards for me to work on in Trello. By 5pm on Monday, I had made my first commits and opened my first pull request against the codebase. I was thrilled! My fears of being a junior developer were unfounded, and I was in the race!

During the first few weeks, I was the hotfix team. The other engineers were wrapping up features for the end of the quarter, and we had some bugs that crept out from under the legacy codebase that needed wrangled. I got really familiar with using Ack and ctags to explore the codebase and dive deeper into methods that I needed to examine. In a short period of time, I became familiar with the main portions of the application, and started to learn where things lived. I fixed real problems in the application, and got to feel a real sense of purpose on the team.

Before the month was over, the whole engineering team flew to Chicago to plan out the next quarter of work. We all brainstormed together to flesh out feature stories with user personas, and although I was the newest member of the team, I got to participate. I was amazed to find that by the end of the week, many of the ideas I contributed to or collaborated on became a part of the product roadmap for the next quarter. Having that sort of involvement so early on made me even more excited about the team I was working with. This was what I had been looking for in a career -- a way to contribute meaningfully to a product that helped people get things done.

The start of the quarter launched the following week, and we worked through pointing stories and assigning features. I found out that I would be working on something besides bugfixes, and once again that nervous excitement was upon me. I was in charge of rewriting and improving how the application dealt with cancellation, reactivation, and standby of accounts in our system and with our payment integration. I was going to be influencing **every user** in our system, and also a portion of our revenue. Me? In charge of how money changes hands? Wow.

Since the end of April, I've been working steadily on this reimplementation. Through the mentorship of my coworkers, I have learned:

- how to collaborate remotely
- how to write cucumber step definitions
- how to use [LightService](https://github.com/adomokos/light-service) to create organizers around small actions that house business logic
- how to write custom validations
- how to stop using `rails g` for anything
- how to know the difference between a mock and a stub
- how to write database-independent tests
- how to make a latte
- where to find the best animated gifs
- that the best coworkers you can have hack late at night with you in the hotel lobby
- and so many other things that have made this a blast

By the end of this week, I'm going to be submitting the last of the pull requests for my feature. By the start of next month, this new implementation will be used by customers all over the country (and Canada too!) The code is shiny, wrapped up in actions and organizers with concise names, the logic backed by unit tests and cucumber features for end-to-end assurance, and every bit of code has had many pairs of eyes on it, helpful bits given to me by everyone on the team through comments on the pull requests, and helpful pairing sessions when I was stuck.

This quarter has been a wild ride. That week between moving from Denver back home, I had no idea what the first 100 days would hold for me as a junior developer. I thought perhaps I would be on the QA team for months before I would be trusted with anything this substantial, and I am so glad I was wrong. This level of responsibility, and this level of trust that the team has given me has empowered me to push my learning to a new level and get more acclimated with our coding conventions and practices. This team has become a part of me, and I have happily become a part of the team that I'll never forget -- because the first 100 days is just the beginning of the rest of my career.

(*Including weekends and a holiday; otherwise, I've been actively committing code to the codebase for 71 days)

> Special thanks to everyone that has helped me in this journey -- [gSchool](http://gschool.it), [JumpstartLab](http://jumpstartlab.com), [Turing](http://turing.io), my fellow classmates, my mentors, and my family and friends. I couldn't have done it without you!
