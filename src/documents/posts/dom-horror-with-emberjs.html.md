---
layout: post
title: DOM Horror with EmberJS
---

So, I've been playing with [EmberJS](http://emberjs.com) over the last few weeks, going through their tutorials and just generally soaking it in. I really appreciate the level of effort and thoughtfulness that Tom Dale and Yehuda Katz have put into this project. I really looked forward to using it more often.

Then, while inspecting the DOM, I found this:

<pre>
&lt;div id=&quot;ember162&quot; class=&quot;ember-view&quot;&gt;
    &lt;h2&gt;Welcome to Ember.js&lt;/h2&gt;

    &lt;script id=&quot;metamorph-1-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
    &lt;script id=&quot;metamorph-0-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
    &lt;ul&gt;
    	&lt;script id=&quot;metamorph-5-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
    	&lt;script id=&quot;metamorph-2-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;li&gt;
			&lt;script id=&quot;metamorph-6-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
			red
			&lt;script id=&quot;metamorph-6-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;/li&gt;
    	&lt;script id=&quot;metamorph-2-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
    	&lt;script id=&quot;metamorph-3-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;li&gt;
			&lt;script id=&quot;metamorph-7-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
			yellow
			&lt;script id=&quot;metamorph-7-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;/li&gt;
		&lt;script id=&quot;metamorph-3-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;script id=&quot;metamorph-4-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;li&gt;
			&lt;script id=&quot;metamorph-8-start&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
			blue
			&lt;script id=&quot;metamorph-8-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;/li&gt;
		&lt;script id=&quot;metamorph-4-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
		&lt;script id=&quot;metamorph-5-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
	&lt;/ul&gt;
	&lt;script id=&quot;metamorph-0-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
	&lt;script id=&quot;metamorph-1-end&quot; type=&quot;text/x-placeholder&quot;&gt;&lt;/script&gt;
&lt;/div&gt;
</pre>

I was completely <em>horrified!</em>  All that code just to render this:

<pre>
&lt;div&gt;
	&lt;h2&gt;Welcome to Ember.js&lt;/h2&gt;
	&lt;ul&gt;
		&lt;li&gt;red&lt;/li&gt;
		&lt;li&gt;yellow&lt;/li&gt;
		&lt;li&gt;blue&lt;/li&gt;
	&lt;/ul&gt;
&lt;/div&gt;
</pre>

And this is the code that's generated right from their starter template! 

Yeah, the ember docs [ explain it well enough ](http://emberjs.com/guides/understanding-ember/keeping-templates-up-to-date/) so I get why it has to be that way. Even so, it really pains me to say this because I really like the philosophy behind Ember, but unfortunately, this is a deal breaker for me. Anyone else feel the same way?

