---
layout: post
title: "Including HtmlAttributes dynamically on mvc helper"
date: 2014-02-05 16:57:57 -0200
comments: true
categories: mvc razor
---

If you are working on a .Net MVC application and need to include a HtmlAttributes dynamically on mvc helper, you should know that its not so simple.

Lets say that you want to include dynamically a disable attribute if one condition is true. Typically, you do this:

```
if(canEdit)
{
    @Html.TextBoxFor(x=> x.Name, new { maxlength = "50" })
}
else
{
    @Html.TextBoxFor(x=> x.Name, new { maxlength = "50", disabled="disabled"})
}
```

We must to agree that its not beautiful. So lets create a extension method to do this job:

```
namespace MyNameSpace
{
    public static class ExtensionMethods
    {
        public static RouteValueDictionary DisabledIf(this object htmlAttributes, bool disabled)
        {
            return htmlAttributes.AppendIf(disabled, "disabled", "disabled");
        }

        public static RouteValueDictionary AppendIf(this object htmlAttributes, bool condition, string attributeName, string attributeValue)
        {
            var attributes = new RouteValueDictionary(htmlAttributes);

            if (condition)
                attributes[attributeName] = attributeValue;

            return attributes;
        }
    }
}
```

Now you only have to call the extension method passing the condition to disable the field:

```
 @Html.TextBoxFor(x=> x.Name, new { maxlength = "50" }.DisabledIf(!canEdit))
```

You also can use the AppendIf to append other attributes:

```
 @Html.TextBoxFor(x=> x.Name, new { maxlength = "50" }.AppendIf(DateTime.Now.Day == 29, "onfocus", "alert('Today is 29, lets eat Gnocchi')"))
```