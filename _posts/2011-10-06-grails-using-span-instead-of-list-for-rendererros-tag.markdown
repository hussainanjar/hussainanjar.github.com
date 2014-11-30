---
layout: post
title:  "Grails: using span instead of list for renderErros tag"
date:   2011-10-06 13:20:00
categories: Grails
---

By default `renderErrors` tag in grails supports `list` or `xml` to display errors, but if we want to display error next to the field as shown below then `list` is not the best way to go.

[![Amount is required](http://blog.hussainanjar.com/wp-content/uploads/2011/10/Screen-Shot-2011-10-06-at-8.36.44-PM1.png "Error Message")](http://blog.hussainanjar.com/wp-content/uploads/2011/10/Screen-Shot-2011-10-06-at-8.36.44-PM1.png)

So to resolve this issue I extended the current grails `ValidationTagLib` and override the tag `renderErrors` to give my own implementation as shown below.

<script src="https://gist.github.com/1267898.js"> </script>