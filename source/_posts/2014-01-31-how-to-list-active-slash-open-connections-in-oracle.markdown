---
layout: post
title: "How to list active / open connections in Oracle?"
date: 2014-01-31 13:19:51 -0200
comments: true
categories: oracle
---

If you are serching for a way to view all open/active connections at oracle, you can  use the v$session view.

```
select * from v$session where username in ('MY_USERNAME');
```

For more information about v$session you can go to the [official documentation](http://docs.oracle.com/cd/B19306_01/server.102/b14237/dynviews_2088.htm).
