---
layout: post
title:  "how git bisect and giant robots saved the day"
date:   2013-09-03 00:00:00 -0700
categories: git debugging tips
---

A couple weeks ago, while I was pushing an update to one of our repositories, I noticed our test suite had a plethora of failing specs. Immediately thinking it was my fault I reverted my changes and ran the test suite again. To my surprise the tests were still failing. Now what? Do I just keep rolling back commits until I find the code that broke the tests? Or, do I start back a day or two and see if they were broken then? Enter Git Bisect!

Git Bisect is a built-in git utility that uses binary search to inspect a set of commits(too numerous to manually checkout) for the code that broke your tests.

I was able to use git bisect, with the help of the blog post from the amazing guys at thoughtbot, to examine all of the commits in question and find the code that broke our tests. It turned out to be a bug in a gem we were using and not our code itself. C'est la vie.

Check out the giant robots smashing into other giant robots post for all the details.
