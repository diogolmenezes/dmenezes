---
layout: post
title: "How to generate a GUID with javascript"
date: 2014-01-22 12:31:41 -0200
comments: true
categories: [javascript]
---

Generate a [GUID](http://en.wikipedia.org/wiki/Globally_unique_identifier) in javascript is definitely not a common task, but if you need it, you can use the below function:

```
function GetGuid() {
    var result='';
    for(var i=0; i<32; i++)
        result += Math.floor(Math.random()*16).toString(16).toUpperCase();
    return result
}
```

If you are searching for an online GUID generator, you can use [this one](/tools/guid.html).