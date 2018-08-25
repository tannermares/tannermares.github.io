---
layout: post
title:  "making a blog you might actually use in 15 minutes...ish"
date:   2013-05-30 00:00:00 -0700
categories: amanda blogs walkthroughs
---

[Amanda](https://github.com/atog/amanda) was first introduced to me on a [ruby5](http://ruby5.envylabs.com/) podcast while driving to work one morning. I had heard of a blog engine that used Dropbox ([scriptogr.am](http://scriptogr.am/)), but I always like the idea of making something myself. It was a relatively painless setup, though there were a couple gotcha's that I would like to write down here, even if only for my own sake.  Now to introduce her.
A simple blog engine powered by [Camping](http://camping.io/).
Posts are written in [Markdown](http://daringfireball.net/projects/markdown/), saved on [Dropbox](https://www.dropbox.com/) and stored in [Redis](http://redis.io/).

### Amanda

Something I really liked about Amanda, which was the main reason I am talking about it here, is that once it's setup, anyone who can manage a folder on Dropbox can manage their own blog, completely custom, completely free. Assuming you have all the major stuff already installed this shouldn't take more than 15 minutes or so. Well let's get to it.

### Before you Begin

This stuff should already be done. If not, there are a plethora of posts about how to get these services setup. These are just a couple of things you need for Amanda to work.

- [Install Git](http://git-scm.com/) ( with [HomeBrew](http://brew.sh/) brew install git )
- Install Ruby 2.0 using either [rbenv](http://octopress.org/docs/setup/rbenv) or [RVM](http://octopress.org/docs/setup/rvm)
- Setup a [Heroku](https://devcenter.heroku.com/articles/quickstart) account and install the Heroku Toolbelt.
- Create a [Dropbox](https://www.dropbox.com/) account.

### DropBox Setup

- [Create Dropbox App](https://www.dropbox.com/developers/apps/create)
- Name your app
- Choose "core"
- Make sure "App folder" is selected
- Click "create app"
- Notate your app key and secret on the next screen

### Ask Amanda Out

`git clone git@github.com:atog/amanda.git`
`cd amanda`
Now that we have Amanda, we can get ready to push to Heroku. First, we'll create a new Heroku app, and install the necessary addons.
`heroku create`
`heroku addons:add redistogo:nano`
Next, we need to create some environmental variables.
`heroku config:set DROPBOX_APP_KEY=your_dropbox_app_key`
Use `heroku config:set` to create the rest of the variables below. You can set all at once or one at a time.

```bash
DROPBOX_APP_SECRET=your_dropbox_app_secret
REDIS_SERVICE=REDISTOGO_URL
AUTHOR=Tanner Mares
TITLE="Tanner Mares' Blog"
SECRET=Some super session secret
REFRESH_PATH=/refresh
```

Finally, we can push up to Heroku.
`git push heroku master`
This step will take a minute or two. Once your terminal is given back to you, run.
`heroku open`
At this point you should be directed to the "authorize app" page on dropbox.
Click "allow".
At this point we don't have any posts so Heroku should return an "Internal Server Error". Let's fix that.

### Write some posts

Create your first few blog posts. You'll need to create at least two posts to start in order to avoid an infinite loop on the home page. Filenames must use the following format: `%Y%m%d%H%M.md` (e.g. 201305301030.md) in the Amanda dropbox folder. First lines must contain the title, date and can contain tags and / or slug. Followed by your post.
e.g.

```
Title: Hello World
Date: 2013-05-29 22:00
Tags: tags, are, comma, separated
Slug: this-slug-is-optional

Hello World, first post!
```

### Refresh

This will sync up your new posts to the redis database and redirect to the home page. Woot! You're done! Well, besides converting the dutch text and maybe adjusting some styles.
I hope this post made it as simple as possible to get your Amanda blog up and running. Be advised, this framework is still in its infancy. There is a minor bug that only occurs when a single post exists (which I have a [pull-request](https://github.com/atog/amanda/pull/1) for). Please contribute to this project with me to make it even more awesome! Thanks!
