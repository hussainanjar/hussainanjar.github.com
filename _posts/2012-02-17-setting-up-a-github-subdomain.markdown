---
layout: post
title:  "Setting up a GitHub subdomain"
date:   2012-02-17 13:20:00
categories: GitHub
---

Setting up a GitHub subdomain to host your html website is very simple.

Start with creating a new repository on GitHub with the project name as **yourusername.github.io**.

Once you have created the repository you need to set it up on your local machine and push a master branch with index.html file. Follow the below steps

```bash
git clone https://github.com/username/username.github.io
cd username.github.io
vim index.html
git add index.html
git commit -m "Added index page"
git push -u origin master
```

When you push changes for the first time it take around 10 mins for your change to be live on Github http://yourusername.github.io
