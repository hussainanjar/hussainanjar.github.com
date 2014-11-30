---
layout: post
title:  "Setting up a GitHub subdomain"
date:   2012-02-17 13:20:00
categories: GitHub
---

**UPDATE:** Below article is no more applicable visit GitHub pages (https://help.github.com/categories/20/articles) for more details

Setting up a GitHub subdomain to host your html website is very simple.

Start with creating a new repository on GitHub with the project name as **yourusername.github.com.**

[![](http://blog.hussainanjar.com/wp-content/uploads/2012/02/Screen-Shot-2012-02-17-at-11.37.44-AM1.png "GitHub new Repository")](http://blog.hussainanjar.com/wp-content/uploads/2012/02/Screen-Shot-2012-02-17-at-11.37.44-AM1.png)

Once you have created the repository you need to set it up on your local machine and push a master branch with index.html file. Follow the below steps

<pre language="perl" line="1">
mkdir hussainanjar.github.com
cd hussainanjar.github.com/
git init
git remote add origin git@github.com:hussainanjar/hussainanjar.github.com.git
vim index.html
git add index.html
git commit -m "Added index page"
git push -u origin master
</pre>

Once you push your branch you will get following email from GitHub.

> Your page has been built. If this is the first time you've pushed, it may take a few minutes to appear, otherwise your changes should appear immediately.

So as the email suggests just wait for few minutes and you will have your own html website hosted on GitHub subdomain. 