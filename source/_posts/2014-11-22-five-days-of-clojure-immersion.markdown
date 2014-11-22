---
layout: post
title: "Five Days of Clojure Immersion at ClojureConj"
date: 2014-11-22 16:24
comments: true
categories: clojure clojureconj learning
---

This past week marks my first deep-dive into Clojure, and it happened to be at clojure/conj in Washington, DC. I had great time, and I want to give an overview of my experience as a newcomer to the community, so that anyone else that may have been intimidated by the parens can be inspired to give it a try.

I had originally registered only for the two-day Intro to Clojure training hosted by Cognitect, and had been looking forward to it for months. I had cracked open a book or two about Clojure here or there, and watched some of the [LispCast videos](http://www.purelyfunctional.tv/intro-to-clojure) in small jolts, but I hadn't taken the time to just sit down with it for a while and really get immersed. The two-day training session seemed like a good way to get the kick in the pants that I needed to get going with the basics. A few weeks ago, two of my co-workers that had registered for the conference portion could no longer attend. I was fortunate enough to have been able to extend my stay with the support of my CTO, and pick up his ticket to the conj. 

After spending Monday traveling, getting used to my surroundings when I arrived, and going on an obligatory tour of downtown DC on a Segway, I settled in for an evening of toying with [vim-fireplace](https://github.com/tpope/vim-fireplace), a plugin that allows for Clojure REPL support inside of vim. I got my environment up and running, and was ready for the first day of class.

When I got to the training session on Tuesday, Kim and [Lynn](https://twitter.com/lynngrogan) from Cognitect were super friendly and got me going on my way. All of the files we'd be working with, including a leiningen project with last Friday's alpha release of Clojure and other dependencies we'd need for the class, were provided to us on a usb drive. [Alex Miller](http://twitter.com/puredanger), of StrangeLoop, LambdaJam, and ClojureWest fame, was our teacher for the course. We spent the first day learning about the REPL, functions, collections, flow control, names and namespaces, a deeper dive into collections, and finally, sequences. Each one of those sections had labs for us to try to solve in the REPL for ourselves, which I felt really helped solidify the concepts for me and helped me get used to the new syntax. 

After our first day of class, Cognitect had organized a class dinner together for anyone that wanted to join. It was great to spend some time with our fellow class-mates and learn about the problems they were trying to solve, and why they were interested in using Clojure to solve them. I had excellent conversations with the group, and was also delighted to find out that Stephanie Hickey was taking the Introductory course with us for a fellowship project at her job. After dinner, I headed home to work some of the exercises in our labs, and rest up for the next day full of information.

On day two, we started out the day full-speed with sequence theory. After sequences, we got into transducers, something I'm glad we covered before the conference, since there were many references during various talks. From there we moved into polymorphism, concurrency, macros, and core.async. By the end of class, we only had enough time to do a cursory cover of web development in Clojure, but I think that introduction was enough to help me understand the basics. With all of that information in that short of a period of time, I was a little surprised that I was able to keep up with the pace. I think Alex's patience and willingness to answer questions helped immensely in my ability to understand the concepts being presented. That evening, I went home and spent some time looking at some of the various resources that Alex gave us at the end of the class for continued learning, and solving problems on [4clojure](http://4clojure.com).

Throughout the conference, I was happy to have had the course right before attending. I felt like I had the vocabulary to understand the presentations, and that many of them were very approachable armed with that knowledge. 

Some of my favorite presentations are already available online (and all will be available at [clojuretv](https://www.youtube.com/watch?v=7lm3K8zVOdY)):

- [Unlocking data-driven systems](https://www.youtube.com/watch?v=BNkYYYyfF48)
- [The evolution of the Emacs tooling for Clojure](https://www.youtube.com/watch?v=4X-1fJm25Ww)
- [Inside Transducers](https://www.youtube.com/watch?v=4KqUvG8HPYo)
- [Helping voters with Pedestal, Datomic, Om and core.async](https://www.youtube.com/watch?v=Ohuadp9S2hg)
- [Exploring four hidden superpowers of Datomic](https://www.youtube.com/watch?v=7lm3K8zVOdY)
-[ Making Games at Runtime with Clojure](https://www.youtube.com/watch?v=0GzzFeS5cMc)
- [Cló: The Algorithms of TeX in Clojure](https://www.youtube.com/watch?v=824yVKUPFjU)
- [Always Be Composing](https://www.youtube.com/watch?v=3oQTSP4FngY)
- [Building a Data Pipeline with Clojure and Kafka](https://www.youtube.com/watch?v=6xlyWjqFDWs)

Throughout the conference -- from the presentations, to the hallway track, to my interactions with people after sessions -- I've observed some very interesting things about the Clojure community as a first-timer.

I was very impressed that everyone was very humble and friendly. I took my introduction courses with Stephanie Hickey, and didn't have a clue until conversations we had much later. I had dinner -- twice -- with authors without knowing that they had written books about Clojure. No one touted themselves as the end-all-be-all of programming, and everyone was super excited and welcoming of my beginner's journey in Clojure. I didn't feel any judgement for showing up to a conference without having really used the language before, and people included me in conversations and answered my questions patiently without sneering at my lack of knowledge. 

Throughout the presentations and the conversations I had with others, I found a recurring theme -- everyone was eager to improve. Many talks presented ideas as "pretty good, but what can we do better?", and then continued to push through to several iterations of the idea and it's evolution. 

It seems that people in this community love what they do, and actively seek to improve on it whenever they can. There are strong ties to the research being done in the computer science world, and it is refreshing to see people pushing on that research, trying to implement it into the language, and reaching new boundaries when putting things into practice. 

There is also a healthy, friendly competition. We heard about several different editors for Clojure code, and all of the presentations provided some humor around the competition, without demeaning or demoralizing the other parties. On Saturday, Zach's talk, Always Be Composing, presented ideas and a library that are a different way of dealing with event-driven abstractions than what is offered in `core.async`, but his presentation and demeanor was one of an openness to explore ideas, not one of righteousness. That is another recurring theme in the community -- in many of the presentations, presenters were soliciting for discussion of the ideas presented; for input and suggestions. This is a different tone than I've experienced in other communities, wherein a presenter will impart a tone of finality on the subject; that whatever is presented is the final draft.

Another interesting theme I observed was that people were seeking a greater clarity of intent in their projects. Through the proper abstractions, they wanted their programs to communicate well to other humans reading the program. This human-centric design is a theme in other circles as well, but it is inspiring to see these ideas about architecture and design thriving in the Clojure community.

Finally, the most exciting thing I observed was how Rich Hickey, undoubtedly look upon as a leader in the community around the language he invented, is still excited and enthused about it. He comes off as geniunely interested in the ideas of others, and is a thinker himself. He is a thoughtful, positive, and entertaining force in the community; full of energy and ideas, and excited in the potential that as the language grows in use, so will the discoveries around what goes into the core of the language. 

It's been an awesome week of Clojure for me, and I'm glad to have taken a deep-dive into it. I feel empowered to take my knowledge of the language to the next level and start building projects with it, to learn the nuances of functional thinking, and to experience the focus on data that is prevelant in this community. Kudos to the event organizers, the speakers, the sponsors and the community for helping even the least-experienced attendees feel welcome and involved. I couldn't have asked for a better experience!
