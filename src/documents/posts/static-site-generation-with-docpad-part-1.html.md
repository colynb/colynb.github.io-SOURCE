---
published: true
layout: post
title: Static Site Generation With Docpad (Part 1)
---

## Introduction

Since this is my first blog entry, I think it makes sense for me to talk about the technology behind it a little. The whole site is statically generated on my Macbook using [Docpad](http://docpad.org/), and deployed to [Github Pages](http://pages.github.com/).

"Going static" seems to be the trend within the coding community, and for good reason. Though static site generators are not at all new, I think a couple development trends have factored into it becoming popular.

**1. Git all the things!**

Maybe it's just me but I really love using Git. It just makes managing my projects so much more sane. Branching, merging, committing, are all now just a natural extension to development that I almost don't even have to think about it anymore. Now that I'm thoroughly accustomed to this kind of workflow, I find myself increasingly frustrated with managing Wordpress blogs. To do any development, I have to maintain at least two different MySQL databases, one for development and one for production. Then you have to repeat everything you did locally on your development box, such as installing plugins, and theme development, just to get your changes into production. With a static site, I can work completely local, commit my statically generated pages into git, and then push them up to my site. One source for all data and html.

**2. The rise in laptop development**

Another big contributing factor in the popularity of static sites is that most developers I know work almost exclusively local. They do all their coding on their laptops. There are so many tools that help with this that it makes it so there really is no reason not to anymore. Logging into your live site through an admin interface, in my opinion seems outdated and cumbersome and open to too many possible security threats. Now that we're all working locally, it's the next logical step to just administer our blogs locally as well.

So, after playing around with a couple different static site generators such as Jekyll and Octopress, I've decided to use Docpad. Docpad is written in Node, while the others are based on Ruby. I like Docpad simply because it's less complicated to use. I like that I can just create a new html file, type out my post and save the file. Docpad takes care of the rest, keeping your pages DRY, while you work. It watches for changes and re-generates all your content out to a separate folder, which can then simply be uploaded to any web server.

In the next post, I will walk you through getting setup with Docpad.
