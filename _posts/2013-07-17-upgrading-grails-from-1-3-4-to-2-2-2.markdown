---
layout: post
title:  "Upgrading Grails from 1.3.4 to 2.2.2"
date:   2013-07-17 13:20:00
categories: Grails
---

This post is about my experience of upgrading Grails application from 1.3.4 to 2.2.2. Before I start listing down changes I had to do for upgrade I would like to mention that initially I tried upgrading it to 1.3.7, 1.3.9 without much success as it started throwing many Hibernate errors in different areas of application which fortunately I didn't face while upgrading to 2.2.2.

As mentioned in Pledbrook blog http://pledbrook.github.io/grails-howtos/en/upgradeToGrails2.html I started of with  deleting the target directory and then ran

> grails upgrade --force

As the web.xml for Grails 2 has changed so re-ran install templates command to replace the old one with the new one. In my case there were no custom changes in web.xml otherwise you should backup the current web.xml and copy your custom changes to the new one.

> grails install-templates

Updated jodaTime dependency to latest version, old one was throwing "no such method null safe" error.

> joda-time-1.6.jar -> joda-time-2.2.jar
> joda-time-hibernate-1.2.jar - > joda-time-hibernate-1.3.jar

Now its mandatory to add **`@Validatable`** annotation in command objects otherwise it throws compilation error.

Its not a good practice to have business logic in controller, service should be used but in my case there was a public method which I had to make private.

**name** and **from** attribute in **_g:select_** are mandatory now.

One of the most weird issue I came across was in some parts of application I was getting error **_java.lang.IllegalArgumentException: wrong number of arguments_** and the reason was I had an event hook in one of my domain class **_afterLoad()_** and when I changed it to **_onLoad()_** it got fixed.

There was some code in the constructor of service which I had to re-factor and move it to other place as that also caused issues.

Also re-factored code in-case a service injected in taglib had a cyclic dependency with other services.

Upgraded rendering plugin from rendering:0.3 to rendering:0.4.4 as it was throwing some plugin descriptor error.

Make sure you also update log configuration where you have defined grails packages as following have changed.

> service -> services
> controller -> controllers
> tagLib -> taglib

As we are using logback instead of log4j so had to exclude plugin grails-plugin-log4j

> `inherits("global") {
>  excludes "slf4j-log4j12", "grails-plugin-log4j"
> }
> `

I hope this helps other planning to upgrade Grails to version 2.