---
published: true
date: 2013-08-24
layout: post
title: Static Site Generation With Docpad (Part 2)
---

<a href="/posts/static-site-generation-with-docpad-part-1.html">< Part 1</a>

<h4>Setting Up</h4>

<p>The simplicity of setting up Docpad was one of the reasons I chose it over Octopress. The Docpad <a href="http://docpad.org/docs/intro">Getting Started Guide</a> is a great intro, so start there. The only difficulty I had was in getting my site deployed to Github Pages, using the Docpad plugin. The Docpad deployment guide makes a lot of assumptions about your level of understanding of how Github Pages works. This is all they provide from the docs:</p>

<pre><code class="lang-coffeescript">npm install --save docpad-plugin-ghpages
docpad deploy-ghpages
</code></pre>

<p>
    This installs a plugin that manages pushing your output to Github. However this assumes that you&#39;ve already created a github repo that the Pages site will be pointing to. It assumes you want to deploy to a <code>gh-pages</code> branch of the repo. This is wrong. To publish a blog to Github Pages, you need to push to your master branch. According to the <a href="https://help.github.com/articles/user-organization-and-project-pages">Github Pages documentation</a>, gh-pages is reserved for project landing pages, not regular site/blog pages.
</p>

<p>
    This is all too confusing. Instead of using the docpad github plugin, I decided to just push the output folder directly to the master branch of my repo using standard git commands. I had to reconfigure Docpad slightly so that the <em>output</em> folder and all the <em>source</em> code were set up separate folders. I recommend setting up your files this way:
</p>

<pre>
<code class="lang-text">~/Sites/colynb.com
    ├── OUTPUT (colynb.github.io.git)
    │   ├── icons
    │   ├── img
    │   ├── index.html
    │   ├── posts
    │   ├── scripts
    │   ├── styles
    │   └── vendor
    ├── SOURCE (colynb.github.io-SOURCE.git)
    │   ├── docpad.coffee
    │   ├── node_modules
    │   ├── package.json
    │   └── src
    │       ├── documents
    │       ├── files
    │       └── layouts
</code></pre>

<p>To do this, you just need to tell Docpad where it should save the output. You do that by modifying the docpad.coffee file. Per the <a href="http://docpad.org/docs/config#available-configuration">config docs</a>, you just need to set the <code>outPath</code></p>

<pre>
<code class="lang-text">outPath: '../OUTPUT'</code>
</pre>

<p>This will allow you to create and maintain two separate repositories, one for the output (which gets pushed to Github Pages), and the other for your source code.</p>

#### Deploying to Github Pages with your own Domain

<p>
    I decided to host my site on Github, primarily because it&#39;s free, but also because it's super convenient to commit and push, then serve everything with the same service.   
</p>

<p>
    As briefly explained above, Github Pages works via a specially named repository dedicated for that purpose. If you create a repository named: <code>[username].github.io</code> anything within the <code>master</code> branch of that repository will get hosted out on <a href="http://[username].github.io">http://[username].github.io</a>. So, for instance, my repository: <code>colynb.github.io</code> is hosted out on <a href="http://colynb.github.io">http://colynb.github.io</a> (which redirects to colynb.com)
</p>

<p>
    The next step is to point your domain to the Github Pages IP address. Currently, this IP address is: <code>204.232.175.78</code> but check the docs just to make sure, since it&#39;s possible it could change. Next, checkout the <a href="https://help.github.com/articles/setting-up-a-custom-domain-with-pages">Setting up a custom domain with Pages</a>, doc. It tells you to create a <code>CNAME</code> text file with your domain name, in the root of your pages. So for me it was like this:
</p>

<pre>
<code class="lang-text">~/Sites/colynb.com
    ├── OUTPUT (colynb.github.io.git)
    │   ├── CNAME <--- contains "colynb.com"
</code></pre>

<p>
    Once you&#39;ve committed that to your repo and pushed it up, and you&#39;ve setup your domain to point to the right IP address, it should take Github about 10 minutes (plus the time for DNS cache to clear which could be an hour or more) to listen for that domain.
</p>

<p>
    And that's it. If you have any questions or need any assistance, leave a comment below or find me on [twitter](https://twitter.com/colynb).
</p>