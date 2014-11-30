---
layout: post
title:  "Import CA root certificate into JDK"
date:   2013-07-13 13:20:00
categories: Java
---

JDK comes with list of CA certificates per-installed. In my case I was trying to access Rest Service over HTTPS from my J2EE app which was using certificate provided by Trustwave which by default is not part of the JDK I was using i.e. 1.6

You can check which certificates are already installed in your JDK using following keytool command

> keytool -list -v -keystore $JAVA_HOME/jre/lib/security/cacerts

I downloaded the missing Trustwave cert from 

> https://ssl.trustwave.com/support/install-certificate-java-generic.php

After downloading I imported the cert into the JDK using following command.

> keytool -import -trustcacerts -alias twroot -file stca.cer -keystore $JAVA_HOME/jre/lib/security/cacerts

It will ask for a password to import the cert, if you haven't changed it by default it is **changeit**

Make sure you restart your web-server after importing the certificate.