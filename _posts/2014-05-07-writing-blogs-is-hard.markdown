---
layout: post
title:  "writing blogs is hard"
date:   2014-05-07 00:00:00 -0700
categories: blogs ghost octopress
---

I hate writing.

I started this blog as an exercise to force myself to write something once a week. Whether it was a programming 'pro-tip' or some other interesting thing I learned that week.

Enter Octopress. Octopress is a great framework built over jekyll. It generates static sites off of markdown, has awesome syntax highlighting for coding samples, tons of plugins to show of my lastest tweets, and can be hosted for free on github pages. It's built with ruby so I thought it would be good practice. Once the setup was complete, however, I found adding a new post to be just enough work to make me not want to do it. As you can see by my post history, I lasted only 4 months until I got bored of the process. It was just enough steps that I would forget the workflow and have to google every step of the way every time. Not Ideal.

Enter Ghost. Ghost is 'Just a blogging platform' and it does at least one thing extremely well, lets me write. You can use the hosted Ghost service and pay $5 a month, only needing to log in and start writting. I wanted to have a little more fun so I opted for the self host method. After looking at Nitrious.io (which I was super stoked on until I noticed I couldn't use a custom domain without upgrading out of the free tier) and a free amazon EC2 instance (which I no longer qualified for since I have had my AWS account for over a year), I decided to host on heroku. The only downside to hosting on heroku was that I would have to link images instead of hosting directly on my Ghost app. Small price to pay for free hosting in my opinion.

Setup was a breeze. Following this walkthrough, I was up and running in less than an hour. I could live without the twitter plugin (which I could style and find a place for if I really wanted), but I really wanted syntax highlighting for my code examples, which Ghost didn't have out of the box. I could install a different theme, but I get overwhelmed with themes and can never decide. So I just wanted to add syntax highlighting to the starting theme. Following a fellow Ghost bloggers post, I was good to go.

The last hurdle was making sure all my existing posts from Octopress got redirected to the Ghost version. Octopress used a tannermar.es/blog structure that I couldn't easily add to Ghost. Luckily I could add dates to my blog links and only had to redirect `tannermar.es/blog/:post` to `tannermar.es/:post`. After googling 301 redirects in express I solved my problem by adding this little snippet to Ghosts `core/server/routes/frontend.js`

{% highlight javascript %}
server.get('/blog/\*', function redirect(req, res){  
 res.redirect(301, req.params[0]);
});
{% endhighlight %}

Hopefully with the ease of not having to google every step to write a post, Ghost has given me to just login and start writing I won't put off posting to a semi-annual event.

[octopress]: https://jekyllrb.com/docs/home
[jekyll]: https://github.com/jekyll/jekyll
[github-pages]: https://talk.jekyllrb.com/
[ghost]: https://ghost.io
