---
published: true
date: 2013-08-2
layout: post
title: Static Site Generation With Docpad (Part 1)
---

#### Introduction

Since this is my first blog entry, I think it makes sense for me to talk about the technology behind it a little. The whole site is statically generated on my Macbook using [Docpad](http://docpad.org/), and deployed to [Github Pages](http://pages.github.com/).

&quot;Going static&quot; seems to be the trend within the coding community, and for good reason. Though static site generators are not at all new, I think a couple development trends have factored into it becoming a popular choice with developers.

<ol>
<li><strong>Git all the things!</strong><br>
 Maybe it&#39;s just me but I really love using Git. It just makes managing my projects so much more sane. Branching, merging, committing, are all now just a natural extension to development that I almost don&#39;t even have to think about it anymore. Now that I&#39;m thoroughly accustomed to this kind of workflow, I find myself increasingly frustrated with managing Wordpress blogs. To do any development, I have to maintain at least two different MySQL databases, one for development and one for production. Then you have to repeat everything you did locally on your development box, such as installing plugins, and theme development, just to get your changes into production. With a static site, I can work completely local, commit my statically generated pages into git, and then push them up to my site. One version control source for both code and data.</li>

<li><strong>The rise in laptop development</strong><br>
 Another big contributing factor in the popularity of static sites is that most developers I know work almost exclusively local. They do all their coding on their laptops. There are so many tools that help with this that it makes it so there really is no reason not to anymore. Logging into your live site through an admin interface, in my opinion seems outdated and cumbersome and leaves your site open to potential security exploits. Now that we&#39;re all working locally, it&#39;s the next logical step to just administer our blogs locally as well.</li>
</ol>

#### So, what is Docpad?

<p>
	Docpad is a static site generator built in [NodeJS](http://nodejs.org/) and [Express](http://expressjs.com/). What this means is that Docpad gives you a set of tools that lets you code your site using templates and layouts, and all the other things you're used to using for building dynamic sites. The difference is that it will generate all your pages as plain old static HTML pages, out to an output folder that can be served by any web server (including through localhost using Express).
</p>

<p>
	I chose Docpad over other popular choices ([Jekyll](http://jekyllrb.com/) and [Octopress](http://octopress.org/)) because it&#39;s less complicated to set up - <em>and it's written in Javascript!</em> 
</p>

<p>
	In the next post, I will walk you through <a href="/posts/static-site-generation-with-docpad-part-2.html">getting setup with Docpad</a> and publishing to Github Pages
</p>