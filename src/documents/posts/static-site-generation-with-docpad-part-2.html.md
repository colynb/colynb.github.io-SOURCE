---
published: true
layout: post
title: Static Site Generation With Docpad (Part 2)
---

<h2>Setting Up</h2>

<p>The simplicity of setting up Docpad was one of the reasons I chose it over Octopress. The Docpad <a href="http://docpad.org/docs/intro">Getting Started Guide</a> is a great intro, so start there. The difficulty I had was in getting my site deployed to Github Pages. The Docpad deployment guide makes a lot of assumptions about your level of understanding of how Github Pages works. This is all they provide from the docs:</p>

<pre>
npm install --save docpad-plugin-ghpages
docpad deploy-ghpages
</pre>

<p>This assumes that you&#39;ve already created a github repo that the Pages site will be pointing to. Also, it assumes you want to deploy to a <code>gh-pages</code> branch of the repo. This is wrong. To publish a blog to Github Pages, you need to push to your master branch. According to the <a href="https://help.github.com/articles/user-organization-and-project-pages">Github Pages documentation</a>, gh-pages is reserved for project landing pages, not regular site/blog pages.</p>
<p>This is all too confusing. Instead of using the docpad github plugin, I decided to just push the output folder directly to the master branch of my repo using standard git commands. Doing this, I ran into a dilemma: I also want to commit all my docpad source code and configuration to github, but I want the out folder (which is inside the docpad folder) to be its own repo. You can&#39;t have a repo inside a repo, at least that&#39;s my experience. To solve this, I configured Docpad to generate all the output to a folder that lives above the root. So now, my folder structure is something like the following:</p>
<pre>
~/Sites/colynb.com
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
</pre>

<p>To do this, you just need to tell Docpad where it should save the output. You do that by modifying the docpad.coffee file. Per the <a href="http://docpad.org/docs/config#available-configuration">config docs</a>, you just need to set the <code>outPath</code></p>
<pre>
outPath: '../OUTPUT'
</pre>

<p>This will allow you to create and maintain two separate repositories, one for the output (which gets pushed to Github Pages), and the other for your source code.</p>
<h2>Deploying to Github Pages with your own Domain</h2>

<p>I decided to host my site on Github, primarily because it&#39;s free, but also because I want eventually grow this site into something more like a wiki rather than a personal journal. Github will allow me to do this by giving community members access to my repo for making pull requests.</p>
<p>As briefly explained above, Github Pages works via a specially named repository dedicated for that purpose. If you create a repository named: <code>[username].github.io</code> anything within the <code>master</code> branch of that repository will get hosted out on <a href="http://[username].github.io">http://[username].github.io</a>. So, for instance, my repository: <code>colynb.github.io</code> is hosted out on <a href="http://colynb.github.io">http://colynb.github.io</a></p>
<p>The next step is to point your domain to the Github Pages IP address. Currently, this IP address is: <code>204.232.175.78</code> but check the docs just to make sure, since it&#39;s possible it could change. Next, checkout the <a href="https://help.github.com/articles/setting-up-a-custom-domain-with-pages">Setting up a custom domain with Pages</a>, doc. It tells you to create a <code>CNAME</code> text file with your domain name, in the root of your pages. So for me it was like this:</p>
<pre>
~/Sites/colynb.com
    ├── OUTPUT (colynb.github.io.git)
    │   ├── CNAME <--- contains "colynb.com"
</pre>

<p>Once you&#39;ve committed that to your repo and pushed it up, and you&#39;ve setup your domain to point to the right IP address, it should take Github about 10 minutes (plus the time for DNS cache to clear which could be an hour or more) to listen for that domain.</p>
</div>