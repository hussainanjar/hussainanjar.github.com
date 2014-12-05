---
layout: post
title:  "Setting Up JAVA_HOME on Linux"
date:   2012-09-25 13:20:00
categories: Linux Java
---

To set the environment variables:

`echo 'export JAVA_HOME=/usr/java/jdk1.6.0_21' &gt; /etc/profile.d/jdk.sh`

`echo 'export PATH=$JAVA_HOME/bin:$PATH' &gt;&gt; /etc/profile.d/jdk.sh`

You have to source the file you just created by typing:

`source /etc/profile.d/jdk.sh`

Test if Java environment is successfully installed by typing in this in the shell:

``` bash
$ java -version
java version “1.6.0_03″
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)
```

You can also use which java to test:

``` bash
$ which java
/usr/java/jdk1.6.0_03/bin/java
```

Reference: http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/