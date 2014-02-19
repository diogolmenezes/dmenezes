---
layout: post
title: "Creating a tooltip box with Css"
date: 2014-02-19 15:59:04 -0300
comments: true
categories: css, jquery
---

When we manipulate edges with CSS, we can see that they are rendered with a 45 degree angles. This means that if we define some edges as transparent, we can modify the appearance of the object.

![Tooltip Image](/images/posts/tooltip1.png)

![Tooltip Image](/images/posts/tooltip2.png)

Therefore, we can create triangles just setting its size to 0 and adjusting the size and transparency of the edges. As larger is the size of the border, greater is the size of the triangle.

![Tooltip Image](/images/posts/tooltip3.png)

```
div {
    width: 0px;
    padding: 0px;
    border:80px solid red;
    border-bottom-color:black;
    border-right-color:blue;
    border-left-color:green;
}
```

If we define 3 as transparent edges, we succeeded in isolating a triangle:

![Tooltip Image](/images/posts/tooltip4.png)

```
div {
    width: 0px;
    padding: 0px;
    border:30px solid transparent;
    border-left-color:blue;
}
```
## Tooltip

Now, using the pseudo-element :before we can place this triangle on the side of a div and create a tooltip box.

![Tooltip Image](/images/posts/tooltip5.png)

```
<p class="tooltip">This is a tooltip.</p>
```

```
.tooltip{
    width:200px;
    padding: 20px;
    background:#963636;
    color:#FFF;
    position: relative;
}

.tooltip:before{
    border:10px solid transparent;
    border-right-color:#963636;
    content:"";
    position: absolute;
    left:-20px;
}
```

You can use a bit of JQuery to display this custom tooltip when the user hovers over a link.

![Tooltip Image](/images/posts/tooltip6.png)

```
<p><a href="#">link <span class="tooltip">This is only a tooltip example.</span></a> with tooltip</p>
```

```
a { position: relative; }

.tooltip {
    display: none;
    width:200px;
    padding: 20px;
    background:#963636;
    color:#FFF;
    position: absolute;
    top:-100px;
    left:-10px;
}

.tooltip:before {
    border:10px solid transparent;
    border-top-color:#963636;
    content:"";
    position: absolute;
    bottom:-20px;
}
```

```
<script type="text/javascript">
    $(function() {
      $('a').hover(function(){
        $(this).find('.tooltip').show();
      }, function(){
        $(this).find('.tooltip').hide();
      });

    });
</script>
```