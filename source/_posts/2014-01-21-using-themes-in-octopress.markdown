---
layout: post
title: "Using themes in octopress"
date: 2014-01-22 23:41:26 -0200
comments: true
categories: [ruby, octopress, jekyll]
author: Diogo Menezes
---

Recently I talked about [how to create a blog with octopress](/blog/2014/01/21/creating-a-blog-with-octopress). Now I will try to teach you how to apply themes in your octopress blog.

The process of configure themes on octopress is very simple, but before you will have to choose witch theme you will want to apply.

You will find various themes [here](https://github.com/imathis/octopress/wiki/3rd-Party-Octopress-Themes) and [here](http://opthemes.com/).

For this example, I chose the [CleanPress](https://github.com/macjasp/cleanpress) theme.

Now the first step is clone the theme repository inside the .themes/ directory of your octopress blog.

```
$ cd my_octo_blog
$ git clone git://github.com/macjasp/cleanpress.git .themes/cleanpress
```

Next, just install the theme and generate the static files this way:

```
$ rake install['cleanpress']
$ rake generate
```
Fire up the webserver and go to <http://localhost:4000>. If everything runs well your blog will be with the new theme.

```
$ rake preview
```
You can create your own theme or edit existing themes too, its easy and makes your blog unique.