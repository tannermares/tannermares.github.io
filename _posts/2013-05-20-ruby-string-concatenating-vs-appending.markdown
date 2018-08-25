---
layout: post
title:  "ruby String Concatenating vs Appending"
date:   2013-05-20 00:00:00 -0700
categories: ruby
---

While reading through the github style guide for ruby, something popped out at me that I considered a little more than just good style. Being that most of my programming experience is in PHP, I have concatenated strings like this

```ruby
# ok for php, BAD for ruby
html = ""
html + "<h1>Page title</h1>"

paragraphs.each do |paragraph|
  html + "<p>#{paragraph}</p>"
end
```

Though this is valid ruby, it should be avoided. Especially when you need to construct large chunks of data. Instead, use `String#<<`, which mutates the string instance in-place and is always faster than `String#+`, which creates a bunch of new string objects.

```ruby
# better and faster
html = ""
html << "<h1>Page title</h1>"

paragraphs.each do |paragraph|
 html << "<p>#{paragraph}</p>"
end
```

If you havn't read it yet, checkout github's [ruby style guide](https://github.com/styleguide/ruby) for more best practices!
