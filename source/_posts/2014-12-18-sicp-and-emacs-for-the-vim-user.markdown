---
layout: post
title: "SICP and Emacs for the Vim user"
date: 2014-12-18 20:58
comments: true
categories: learning, sicp, functional, emacs, scheme
---

### What is SICP?

[SICP](http://mitpress.mit.edu/sicp/), also known as 'Structure and Interpretation of Computer Programs', is a textbook by Harold Abelson and Gerald Sussman that was written to be used with the Computer Science 100 level course at MIT. For the last two decades, it has been the cornerstone of many student's introduction to how computer programs work. It is one of the few textbooks out there that, although originally written in the 1985, still applies in our field today. Although SICP does teach computer science concepts through the use of Scheme, the language that is being used is not as important as the concepts presented. Many fundamentals courses these days focus more on the language, and this is often cited as the reason why SICP is still relevant. After asking many programmers in several communities what their favorite book is on programming, SICP came up time and time again. As such, I am embarking on the journey to learn and practice through this textbook. But first, I need to get my environment set up. And that's where the interesting findings began!

### Vim, tmux, racket, and a few other things

On a daily basis, my toolset mainly involves vim, tmux, and bash. I'm fairly efficient in using my tools, and I was eager to get going with my setup so that I could start doing exercises in the book. After some digging around and trying of things, I realized that although my Vim setup is fine with lisp-y languages (due to plugins I installed for use with Clojure), that in-line evaulation and quick access to the REPL was another story. In Clojure, `vim-fireplace` does the heavy lifting of giving you in-line evaluation, and keeping a REPL running in the background. However, when using MIT-Scheme (the language used by the book and in the [MIT Open Courseware course](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-001-structure-and-interpretation-of-computer-programs-spring-2005/), I thought I could get around this by running a tmux session split with panes for the Scheme REPL itself, and for my editor in the other. I quickly found that the Scheme REPL in tmux misbehaves when using arrow keys, option or alt to navigate around the text. I had also run across a few blog posts that listed struggles using MIT-Scheme with Vim, and in the end many of those folks chose to use Racket instead, for better editor integration. In an effort to stick with MIT-Scheme, I decided to look elsewhere: to Emacs.

### Emacs: A different beast

With Emacs, you have an entire environment. Different from Vim, you can run entire programs within Emacs. I accidently began an IRC client in there. You can even play a game of tetris using `M-x tetris`. Having never seen someone use Emacs, when I first downloaded it on Monday, I was in for a surprise. I spent a little time with the main tutorial (similar to vimtutor in Vim, but for Emacs), and began to familiarize myself with the main concepts. But I felt clumsy when editing code. I have so much muscle memory build up around Vim, and that would be hard to un-learn while playing with a new language and learning other new concepts. So I recalled that [Chris Houser](http://twitter.com/chrishouser) mentioned at dinner during ClojureConj that Evil-mode (the vim keybinding compatability package for Emacs) was pretty good, and he even re-stated it in a tweet when I was getting started:

<blockquote class="twitter-tweet" lang="en"><p><a href="https://twitter.com/pzula">@pzula</a> Don&#39;t forget evil-mode. It&#39;s good!</p>&mdash; Chouser (@chrishouser) <a href="https://twitter.com/chrishouser/status/544713565479788544">December 16, 2014</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

So, having already completely copied the setup from Clojure for the Brave and True, I realized I had no idea how customizations work in Emacs, and my inital attempts at installing Evil-mode were failing me so I blew the entire directory away, re-installed emacs using homebrew, and started fresh in order to get what I needed.

Your mileage may vary, depending on how you've set up your system, but I decided to outline the steps I took in order to create an environment where I, as a vim user, could effectively get around Emacs using MIT-Scheme (on OSX) and have everything I need at my fingertips for working through the problems in SICP. For those experienced in these things (Emacs and such), I welcome feedback and corrections along the way. I'm only 4 days young in the environment! (And thank you to Chris Houser for the encouragement and quick walkthrough!)

### Get MIT-Scheme

The best way I found to get MIT-Scheme in a format that doesn't need modification for Emacs is using homebrew:

`brew update && brew install mit-scheme`

Then, type `scheme` in your shell and see if you get a response like so:

```
MIT/GNU Scheme running under OS X
Type `^C' (control-C) followed by `H' to obtain information about interrupts.

```

If so, you're good to proceed to the next step. If not, either try to install via homebrew again, or check your path.

### Next, get some Emacs!

I installed Emacs via homebrew as well. The first time around, I went to the Emacs wiki and downloaded the executable OSX `.app`, but I live and breath in my terminal, so I chose to remove that version and reinstall via homebrew as well:

`brew install emacs`

This will get you the latest version of Emacs. You should now be able to run it from your terminal using `emacs`. If something fails, either try to reinstall via homebrew, or check your paths.

Once you have Emacs up and running, take a look at the help guide that is on the splash page. Then, print out the guide below and keep it handy during this journey!

### Print out this reference guide to Emacs

[GNU Emacs Reference Guide](http://www.ic.unicamp.br/~helio/disciplinas/MC102/Emacs_Reference_Card.pdf) -- You won't need it all of the time, but there are times when your vim keybindings won't get you what you want!

### Install Evil-mode

After you've poked around and used to commands, and your fingers get tired of using C-x for everything, make the decision on whether you're going to stick to purely Emacs, or if you want to the add the vim keybindings layer provided in Evil-mode.
