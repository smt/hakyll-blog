---
date: 2014-02-11 19:28:52
title: Gulp and Browserify
tags: JavaScript, Mad Coding, Node.js
---

Just a quick write-up of some things I've been playing with lately.

A few weeks ago, at lunch with some old coworkers, someone mentioned that
[gulp][1] might just be the new hotness that steals Grunt's thunder. More
recently, I was inspired by [Martin Genev][2] to look into the gulp build
system and [Browserify][3]. I'm pretty impressed with what I've seen of gulp
thus far, but I feel the bigger story by far is Browserify.

**Update (2014-04-09):**
[Dan Tello][4] has posted a [far superior contribution][5] on this topic. The
examples he gives are really&nbsp;compelling.

## gulp

I've been on several projects now that use the Grunt build system, and I'm not
trying to criticize Grunt -- in many ways, it was a Godsend that saved us from
the hell of Makefiles and build.xml files. However, I always found configuring
Grunt to be a major chore, and I was always bad at it. The up-front
configuration work can be pretty intimidating.

In contrast, [gulp][1] uses conventions similar to node.js streams. I'm no
expert with using streams myself, but to be able to pipe operations into other
operations, Unix-style, is quite intuitive. Writing a task in gulp is nearly as
simple and natural as pseudo-coding what you want it to do.

In this example, I defined a task to build and concatenate my JavaScript source
into a single file (dist/built.js), adding a file watcher for good measure.
Nice!

```javascript
var gulp = require('gulp');
var util = require('gulp-util');
var concat = require('gulp-concat');
var browserify = require('gulp-browserify');

gulp.task('scripts', function (cb) {
    gulp.src('./src/app.js')
        .pipe(browserify({
            basedir: './',
            debug: !util.env.production
        }))
        .pipe(concat('built.js'))
        .pipe(gulp.dest('./dist/'))
});

gulp.task('watch', ['scripts'], function () {
    var watcher = gulp.watch('./src/**/*.js', ['scripts']);
    watcher.on('change', function (event) {
        console.log('File ' + event.path + ' was ' + event.type + ', building scripts...');
    });
});

gulp.task('default', ['scripts', 'watch']);
```

## Browserify

I honestly don't think I can do [Browserify][3] any justice by attempting to
explain it here, but it's basically a library that allows you to use core node
modules, npm modules, and your own modules written in node.js style **in the
browser**.

I've been a proponent of AMD and RequireJS for some time, but when it comes to
writing modules in JavaScript, here's my big question: Why not use the same
conventions for the browser as for node.js, with minimal, if any, boilerplate
needed?

Browserify lets you do that. I wrote 3 or 4 modules, using node.js-style
`require` statements for dependencies, and exposing what I needed to with
`module.exports`. With very little configuration (see the gulpfile.js example
above), Browserify wrapped all my modules appropriately, and built them to
a single JS file, which I loaded in the browser. It worked. It was glorious.
The blinders were off.

My experience with Browserify thus far has only been with modules I've written
myself. I haven't even scratched the surface of using an npm module in the
browser yet. That will be my next experiment. I'm genuinely excited.

  [1]: http://gulpjs.com
  [2]: http://www.100percentjs.com/just-like-grunt-gulp-browserify-now/
  [3]: http://browserify.com
  [4]: http://viget.com/about/team/dtello
  [5]: http://viget.com/extend/gulp-browserify-starter-faq
