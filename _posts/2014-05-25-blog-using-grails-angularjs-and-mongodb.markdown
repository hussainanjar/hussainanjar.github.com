---
layout: post
title:  "Blog using Grails, AngularJS and MongoDB"
date:   2014-05-25 13:20:00
categories: AngularJS Grails MongoDB
---

I have created simple blog (http://gamb.herokuapp.com/) using [Grails](http://grails.org/), [AngularJS](http://angularjs.org/) and [MongoDB](http://mongodb.org/). This blog uses grails asset pipeline plugin to minify, uglify and bundle resources. Minification of CKEditor is disabled as it was causing some errors. You can find the source on [GitHub](https://github.com/hussainanjar/grails-angular-mongodb-blog).

You can use following credential to login to admin area of the blog.
> [http://gamb.herokuapp.com/admin/](http://gamb.herokuapp.com/admin/)
> 
> Username: admin
> 
> Password: admin123
Note: To keep the integrity of the blog updates and deletes have been disabled.

Two different grails layout are created to initialize frontend and backend app. You can find following entries in _[URLMappings](https://github.com/hussainanjar/grails-angular-mongodb-blog/blob/master/grails-app/conf/UrlMappings.groovy#L31-L32) _file pointing to path of these apps.
> _"/"(view:"/blog/index")_
> 
> _"/admin"(view:"/admin/index")_
Frontend and Backend of the application are seprated in two different folders.

All the assets and angular views for Frontend can be found in following path
> gamb/grails-app/assets/javascripts/blog.js (Asset pipeline frontend manifest)
> 
> _gamb/grails-app/assets/javascripts/blog/* _
> 
> _gamb/grails-app/assets/stylesheets/blog/*_
> 
> _gamb/web-app/blog/* (Angular JS html views)_
All the assets and angular views for Backend can be found in following path
> gamb/grails-app/assets/javascripts/admin.js (Asset pipeline backend manifest)
> 
> _gamb/grails-app/assets/javascripts/admin/* _
> 
> _gamb/grails-app/assets/stylesheets/admin/*_
> 
> _gamb/web-app/admin/* (Angular JS html views)_
All angular plugins are installed using [bower](http://bower.io/). Just goto dir _gamb/grails-app/assets/_ and run following command to install additional plugins.
> bower install <package>

### Key Plugins of Grails

*   [Asset Pipeline](http://grails.org/plugin/asset-pipeline) - for managing static resources
*   [MongoDB GORM](http://grails.org/plugin/mongodb) - for connecting to MongoDB database
*   [Spring Security](http://grails.org/plugin/spring-security-core) - for access control
*   [Spring Security Rest](http://grails.org/plugin/spring-security-rest) - for token based authentication
Following plugin are purely for deploying on Heroku

*   WebXML
*   Cloud Support
*   [Heroku](http://grails.org/plugin/heroku)

### Key Plugins of Angular

*   Angular route - for manging routes
*   Angular sanitize - for encoding html written in posts
*   Angular resourece - for communicating with APIs
*   Angulartics - for Google Analytics tracking
*   Angular http auth inteceptor - for authentication and intercepting authorized requests
*   Angular bootstrap - Twitter bootstrap
Please leave your valuable comments below.

**Note: **You may have to refresh the hosted blog at heroku couple of times if you are the 1st one accessing it in the last 2 hours as the free version of heroku goes to sleep after a while.