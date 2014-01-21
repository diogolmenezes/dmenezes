---
layout: post
title: "Creating ER diagram with Oracle Sql Developer"
date: 2014-01-21 15:25:28 -0200
comments: true
categories: [oracle]
author: Diogo Menezes
---

Today I needed to create a ER diagram for my oracle database, and found that the Oracle Sql Developer is not so intuitive for this task.

First you will have to open Oracle Sql Developer and go to:

```
    File → Data Modeler → Import → Data Dictionary → select DB connection (or add if none) → Next → select your schema and tables
```

![Alt text](/images/posts/diagram-sql-developer-1.png)

## Updating the diagram

If after making the diagram, you want to change it with the most recently database changes, you will need to select the changed table, click the right mouse button and choose Synchronize with Data Dictionary.

![Alt text](/images/posts/diagram-sql-developer-2.png)

## Exporting the diagram

For export the diagram to image, PDF or SVG, you have to go to:

```
File → Data Modeler → Print Diagram → and chose you option 
```

![Alt text](/images/posts/diagram-sql-developer-3.png)