---
layout: post
title: "How to open links at native browser using cordova"
date: 2014-11-22 17:06:53 -0200
comments: true
categories: [all, cordova, mobile]
author: 'Diogo Menezes'
---

By default the links in cordova apps don't open at phone native web browser.

To do this you have to install the inappbrowser plugin:

```
$ cordova plugin add org.apache.cordova.inappbrowser
```

And then you can use _system target to open the links in native browser:

```
<a href="http://tripolist.com" target="_system">Open Tripolist</a>

or

window.open("http://tripolist.com", "_system");
```

