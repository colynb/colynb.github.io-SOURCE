---
layout: post
date: 2013-11-20
title: Getting Started with Gulp
---

I recently discovered a new javascript based build automation tool called [Gulp](https://github.com/wearefractal/gulp) by [@wearefractal](http://twitter.com/wearefractal). It's extremely simple to learn and use and can easily compete with gruntjs for a variety of different projects. It's so easy you'll be a Gulp expert after watching these [slides](http://slid.es/contra/gulp)

### Installing

In your project folder install the gulp module:

```npm install gulp```

Next, download a [gulp plugin](https://npmjs.org/search?q=gulpplugin) like [gulp-minify-css](https://npmjs.org/package/gulp-minify-css) or [gulp-swig](https://npmjs.org/package/gulp-swig)

```npm install gulp-minify-css gulp-swig```

Then create a ```Gulpfile.js``` file.

```
// Gulpfile.js

var gulp = require('gulp');
var swig = require('gulp-swig');
var minifycss = require('gulp-minify-css');

// compile, minify, and copy templates
gulp.task('templates', function(){
  gulp.src("./src/templates/*.swig")
    .pipe(swig())
    .pipe(gulp.dest("./public/"));
});

// minify and copy styles
gulp.task('styles', function(){
  gulp.src("./src/assets/css/*.css")
    .pipe(minifycss())
    .pipe(gulp.dest("./public/assets/css"));
});


gulp.task('default', function(){
  gulp.run('templates', 'styles');

  // watch files and run scripts if they change
  gulp.watch("./src/templates/*.swig", function(event){
    gulp.run('templates');
  });

  gulp.watch("./src/assets/css/*.css", function(event){
    gulp.run('styles');
  });

});

```

This gulp file has 3 tasks: swig template compilation (templates), css minification (styles), and default (default). Each can be run on the command line separately:

```gulp templates``` or ```gulp styles``` or just the default ```gulp```

In this example, the default task runs both the templates and styles tasks plus starts a watcher method that watches for changes to particular files and then runs a specified task when the file changes.
