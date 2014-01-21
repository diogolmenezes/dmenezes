---
layout: post
title: "Creating a blog with Octopress"
date: 2014-01-21 00:17:04 -0200
comments: true
categories: [ruby, octopress, jekyll]
author: Diogo Menezes
---

[Octopress](http://octopress.org/) is a cool framework for [jekyll](https://github.com/jekyll/jekyll)
a blog-aware, static site generator in [Ruby](https://www.ruby-lang.org/pt/) that allows you to create a static site based in templates, and markdowns files.

The effort to create a blog using Octopress is very small. First, you will need to clone the [repository on GitHub](https://github.com/imathis/octopress):

```
$ git clone https://github.com/imathis/octopress.git my_octo_blog
```

Then you will need to install the bundler and all the project dependences. If you are using RVM, I recommend that you use a new gemset for this process.

```
$ cd my_octo_blog
$ gem install bundler
$ bundle install # download and install all project dependences
$ rake install   # install the default octopress theme
```

Now you can generate the static site and then preview the blog at <http://localhost:4000>:

```
$ rake generate # Generates posts and pages into the public directory
$ rake preview  # Mounts a webserver at <http://localhost:4000>
```

The rake comand allows you to do many tasks, and you can see what are these tasks using the command **rake list**:

```
$ rake list # view all rake tasks

Tasks: clean, copydot, deploy, gen_deploy, generate, install, integrate, isolate, new_page, 
new_post, preview, push, rsync, set_root_dir, setup_github_pages, update_source, update_style, 
watch
```

So, lets create our first post:

```
$ rake new_post['My first post']
mkdir -p source/_posts
Creating new post: source/_posts/2014-01-21-my-first-post.markdown
```

The rake new_post task created the markdown file **source/_posts/2014-01-21-my-first-post.markdown** with the content:

```
layout: post
title: "My first post"
date: 2014-01-21 11:14:44 -0200
comments: true
categories:
```

>* **layout**   - Is the page layout for the post. This layout file is located at the source/_layouts directory, and you can customize it if you want.
>* **title**    - Is the post title
>* **date**     - Is the post creation date
>* **comments** - Indicates if the comments are allowed for this post (true/false)
>* **categories** - Are the post categories, for example [all, job, great]
>* **author** - Is the post author


Now that we know how a post is made, lets write:

```
---
layout: post
title: "My first post"
date: 2014-01-21 11:14:44 -0200
comments: true
categories: [all, job, great]
author: 'Diogo Menezes'
---

Nice, this is my first post. :)

```

Lets preview the result on browser at <http://localhost:4000>.

```
$ rake preview
```

## Deploy on GitHub Pages

Your blog is working on localhost but obviously you want to put it on the internet, dont you?

Fortunately, the GitHub has the [GitHub Pages](http://pages.github.com/), a service that allow you to host your site directly from your GitHub repository.

For this you will need to create a new repository named username.github.io, where username is your username (or organization name) on GitHub.

Then execute the rake setup_github_pages command to conect your blog with the GitHub repository. On this step you will need to put the URL of the new repository (http://github.com/username/username.github.io.git)

```
$ rake setup_github_pages
```

After it you will have to generate the static content and then deploy the blog to GitHub Pages.

```
$ rake generate
$ rake deploy
```

Now, fire up a browser and go to <http://username.github.io>. Give it a couple of minutes for your page to show up—there will be a delay this very first time. In the future, changes will show up pretty much instantly.

## Using a custom domain  with GitHub Pages

GitHub Pages allows you to direct a domain name of your choice at your Page.

Let's say you own the domain example.com, and you would like to use it for your Pages. 

Just create a file named CNAME in the root of your pages (source/) and put the domain (or subdomain) into the file:

```
example.com
```

Next you will need to set up your DNS to point to your GitHub Pages address (<http://username.github.io>)

This process can take a couple of minutes. 

For more information about how to use custom domains you can go to the [official doc](https://help.github.com/articles/setting-up-a-custom-domain-with-pages).

In the next post I will write more about the configuration file (_config.yml), rake, and how to use custom themes in octopress.

If you have questions, comments or suggestions about this article, let me know.