---
layout: post
title: "Getting a New Development Environment Up &amp; Running on Mac OSX"
date: 2013-09-05 21:14
comments: true
categories: environment
---
Getting a new computer can be fun, but it also means a lot of work. Between running into bugs, new versions of software running amok, and documentation from various sources on the big, bad internet just not lining up, it can quickly go from being fun to just being plain frustrating. 

I had a few of those moments myself in the last couple days, so I thought I'd share with other journeymen and women some of the core items I get set up on a new machine. Perhaps a few of the snippets may help you get out of a snag, or maybe you'll find a new tool to love.

## In a loose order of importance

1. The very first thing I installed was [Alfred](http://www.alfredapp.com/). If you love Spotlight, go ahead and stick with it, but I love the flexibility of Alfred for getting around, doing math for me, and lots of other tasks that usually take more than two keystrokes. 

2. [Firefox](http://www.mozilla.org/en-US/firefox/fx/#desktop) & [Chrome](https://www.google.com/intl/en/chrome/browser/), to have browsers to test in. I primarily use Chrome in my daily work, and only every touch Safari for testing.

3. A few extensions for Firefox and Chrome include [Pocket](http://getpocket.com) (for saving things to read later), [Web Developer Toolbar](https://addons.mozilla.org/en-US/firefox/addon/web-developer/), [Firebug](https://addons.mozilla.org/en-US/firefox/addon/firebug/?src=search), and [Personal Blocklist for Chrome](https://chrome.google.com/webstore/detail/personal-blocklist-by-goo/nolijncfnkgaikbjbdaogikpmpbdcdef?hl=en) (this one helps me block anything by w3cschools.com, because most of the time, that site does not promote best practices)

4. [Evernote](http://www.evernote.com) helps me keep track of everything -- from grocery lists to bug fixes. Whenever I think of something, I can pop open Evernote, and be sure that when I need to come back to it, I can access it from anywhere. I love this app, and it's free!

5. [Skype](http://www.skype.com) helps me keep in touch with other developers, friends, and family around the world.

6. [Sublime Text 2](http://www.sublimetext.com) is my editor of choice. Although I know there are many proponents of Vi/Vim and other non-GUI editors, my focus right now is on learning to become a better programmer. I'll focus on learning those later.

7. Here are my favorite Sublime Text 2 packages:
	- [Emmet](http://docs.emmet.io/)
	- [NetTuts Fetch](http://net.tutsplus.com/articles/news/introducing-nettuts-fetch/)
	- [Advanced New File](https://tutsplus.com/lesson/lightning-fast-folder-and-file-creation/)
	- [Sidebar Enhancements](https://tutsplus.com/lesson/sidebar-enhancements/)
	- [Sublime Linter](https://github.com/SublimeLinter/SublimeLinter)
	- I also enable Sublime to be opened from the command line (this is where the Vim users scoff).
	Run this in your terminal: `ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" /bin/subl
`	Now you will be able to open any file from the Terminal with `$ subl filename-here.html`

8. You can use Sublime Text 2 as your Markdown editor for blog posts, but I prefer the immediate feedback of [Mou](http://mouapp.com). 
	-  I find that I'm often at the command line wanting to use Mou, but don't feel like going through the GUI to open a new file or the app itself, so I set up an alias in my `.bash_profile` as follows: `alias mou="open /Applications/Mou.app"`. Now whenever I `rake` a new post in Octopress, I can immediately open it with Mou without having to take my hands off the keyboard.
	
9. Speaking of the command line, I have a few little modifications I like to make to the Terminal 





