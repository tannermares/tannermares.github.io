---
layout: post
title:  "why I use RubyMine...For now"
date:   2013-08-09 00:00:00 -0700
categories: ruby editors rubymine IDE
---

Hello Everyone! I have been struggling with a new topic to write about this last month. Since I couldn't think of any mind blowing code samples, I have decided to show you my current development environment. Specifically, my text editor. For about a year or so I have been using Sublime Text as my text editor of choice. With its virtually non-existent learning curve and slew of plugins, it is a god among text editors.

It wasn't until about 4 months ago when I started at Planning Center Online, who utilizes Test Driven Development, that I found myself constantly switching between my terminal and editor. This was problematic as my text editor could only take half of my screen so my instance of Guard (file system monitor, runs rspec tests on file save), my development log, and rails console instance could be seen at the same time. I like having a full screen editor so I can have my files and tests open at the same time. This was my main reason for checking out RubyMine.

RubyMine is an IDE (integrated development environment) from the team at JetBrains. I don't think I could write less than several pages if I listed all the features this software has to offer. So I'll just inform you of the features I have found most helpful.

After installing RubyMine there were a couple things I had to immediately change. The first was the light color scheme. Luckily, there is a built in dark mode, Darcula, that pleased me with no modification.

The second was changing the color scheme to my current favorite, Monokai.

Much better! Now that it was as visually pleasant as Sublime, I could focus on making my environment easier to work with. I started by creating a Guard task so that I could watch my tests. The one tricky part about this was because I use rbenv, the guard executable is not in its normal place. Simply running which guard while in my current repo led me to this setup.

Then simply running the "Guard" configuration will launch my Guard instance and keep it running in a tab I can hide when I want. Doing a similar setup for a generic rails console and resqueinstance, I can have all my background processes running in the same window I am working in. From the configuration menu, I can also run a local instance of my app and keep track of the development logs. All together it looks like this.

With this setup I have tabbed access to everything I had used the terminal for. Something worth mentioning, I use pow to spin up local web severs. RubyMine will also spin up a thin web server and map your app to 0.0.0.0:3000 for you when you run the environment from the configuration list. Sweet!
A couple of things I have used on a daily basis that have been big time savers are the code inspector,

built in ruby style guide warnings,

git integration (specifically history, diff viewing and conflict resolution),

live stacktrace links to file and line numbers,

quick documentation links,

and command clicking method names to go to their definitions.

So far I have had an awesome experience using RubyMine. Though it is not very cool to use an IDE right now, I feel that it will make me a more efficient and productive programmer. I can even install a VIM plugin if I find myself reminiscing of modal editing. I hope this gave you a little insight into the world that is IDEs and what they can offer a developer in today's web environment.
