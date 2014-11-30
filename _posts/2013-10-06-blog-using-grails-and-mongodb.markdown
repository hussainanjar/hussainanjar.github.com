---
layout: post
title:  "Blog using Grails and MongoDB"
date:   2013-10-06 13:20:00
categories: Grails MongoDB
---

I have created a simple blog using Grails and MongoDB (demo hosted at [heroku](http://grails-mongodb-blog.herokuapp.com)). You can find the source code for this blog at [github](http://github.com/hussainanjar/grails-mongodb-blog).

You can also browse around the admin module of the blog using following credentials.
> URL: http://grails-mongodb-blog.herokuapp.com/admin/
> Username: visitor
> Password: visitor123
Following are the list of plugins I have used in this project.

**Default Plugins**

*   Jquery 1.8.3
*   Resources 1.2
*   Tomcat 2.2.4
*   Cache 1.0.1

**Security Plugins**

*   Spring Security 1.2.7.3

**Cloud Plugins**

*   Webxml 1.4.1
*   Heroku 1.0.1
*   Cloud Support 1.0.8

**Other Plugins**

*   ckeditor 3.6.6.1.0

**Note: **You may have to refresh the hosted blog at heroku couple of times if you are the 1st one accessing it in the last 2 hours as the free version of heroku goes to sleep after a while.