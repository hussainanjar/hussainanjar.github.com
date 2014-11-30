---
layout: post
title:  "Installing tomcat6 on CentOS"
date:   2011-04-15 15:05:00
categories: linux tomcat
---

<strong>Make sure you replace software versions used in this blog with the one that you download.</strong>

<span style="text-decoration: underline;"><strong>Installing JAVA</strong></span>

Before installing tomcat you need JDK and JRE 6 installed on your server. You can download them from following links with wget in your home (~) directory. Make sure you download the .bin file and not the rpm.bin.

<a href="http://java.sun.com/javase/downloads/widget/jdk6.jsp" target="_blank">JDK</a>

<a href="https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u18-oth-JPR@CDS-CDS_Developer" target="_blank">JRE</a>

Download JDK
<blockquote>wget jdk-6u21-linux-x64.bin?AuthParam=1302867934….bin</blockquote>
Download JRE
<blockquote>wget jre-6u18-linux-x64.bin?AuthParam=130286…bin</blockquote>
Most probably the downloaded file will have URL parameters attached to them, you can rename these files using the mv command
<blockquote>mv jdk-6u21-linux-x64.bin?AuthParam=1302867934….bin jdk-6u21-linux-x64.bin

mv jre-6u18-linux-x64.bin?AuthParam=130286…bin jre-6u18-linux-x64.bin</blockquote>
now create a directory for installing JDK
<blockquote>sudo mkdir /user/java

cd /usr/java</blockquote>
Execute the JDK installation file
<blockquote>sudo sh ~/jdk-6u21-linux-x64.bin</blockquote>
Press Enter to continue. Now install the JRE
<blockquote>sudo sh ~/jre-6u18-linux-x64.bin</blockquote>
A license agreement will be displayed press SPACE to continue through the license and at the end enter YES to proceed with the installation

<span style="text-decoration: underline;"><strong>Installing ANT</strong></span>

You can download the tar.gz file under the Current Release of Ant section from the following link

<a href="http://ant.apache.org/bindownload.cgi" target="_blank">ANT</a>

Download ant under the /usr/share directory
<blockquote>cd /usr/share

sudo wget http://mirror.nyi.net/apache//ant/binaries/apache-ant-1.8.2-bin.tar.gz</blockquote>
Extract the downloaded file
<blockquote>sudo tar -xzf apache-ant-1.8.2-bin.tar.gz</blockquote>
Create symbolic link for ant so other applications can find it
<blockquote>sudo ln -s /usr/share/apache-ant-1.8.2/bin/ant /usr/bin</blockquote>
<span style="text-decoration: underline;"><strong>Installing Tomcat</strong></span>

You can download the latest core version (.tar.gz) under the Binary Distributions section from the following link

<a href="http://tomcat.apache.org/download-60.cgi" target="_blank">Tomcat6 </a>

Download tomcat under /usr/share directory
<blockquote>cd /usr/share

sudo wget http://apache.mirrors.redwire.net/tomcat/tomcat-6/v6.0.32/bin/apache-tomcat-6.0.32.tar.gz</blockquote>
Extract the downloaded file
<blockquote>sudo tar -xzf apache-tomcat-6.0.32.tar.gz</blockquote>
Now we need to set <strong>JAVA_HOME</strong> for tomcat by editing catalina.sh file
<blockquote>cd /usr/share/apache-tomcat-6.0.32/bin

sudo vi catalina.sh</blockquote>
above command will open catalina.sh in the vi editor. Press <strong>i</strong> key to enter the insert mode and just below the line <strong>#!/bin/sh</strong> enter the <strong>JAVA_HOME</strong> path.
<blockquote>JAVA_HOME=/usr/java/jdk1.6.0_21</blockquote>
Press <strong>ESC </strong>to leave the insert mode and enter <strong>:wq</strong> to save and quit the file. Now test the tomcat installation
<blockquote>cd /usr/share/apache-tomcat-6.0.32/bin/

sudo ./startup.sh</blockquote>
If the installation was successful you should see something like this
<blockquote>Using CATALINA_BASE:   /usr/share/apache-tomcat-6.0.32

Using CATALINA_HOME:   /usr/share/apache-tomcat-6.0.32

Using CATALINA_TMPDIR: /usr/share/apache-tomcat-6.0.32/temp

Using JRE_HOME:        /usr/java/jdk1.6.0_21

Using CLASSPATH:       /usr/share/apache-tomcat-6.0.32/bin/bootstrap.jar</blockquote>
<span style="text-decoration: underline;"><strong>Create tomcat as a Service</strong></span>

Create a new file <strong>tomcat </strong>under /etc/init.d directory
<blockquote>cd /etc/init.d/

sudo vi tomcat</blockquote>
above command will open a vi editor, press <strong>i</strong> key to enter the insert mode and copy paste in the following

{% highlight bash %}
#!/bin/bash
# chkconfig: 234 20 80
# description: Tomcat Server basic start/shutdown script
# processname: tomcat
JAVA_HOME=/usr/java/jdk1.6.0_21
export JAVA_HOME
TOMCAT_HOME=/usr/share/apache-tomcat-6.0.32/bin
START_TOMCAT=/usr/share/apache-tomcat-6.0.32/bin/startup.sh
STOP_TOMCAT=/usr/share/apache-tomcat-6.0.32/bin/shutdown.sh
start() {
echo -n "Starting tomcat: "
cd $TOMCAT_HOME
${START_TOMCAT}
echo "done."
}
stop() {
echo -n "Shutting down tomcat: "
cd $TOMCAT_HOME
${STOP_TOMCAT}
echo "done."
}
case "$1" in
start)
start
;;
stop)
stop
;;
restart)
stop
sleep 10
start
;;
*)
echo "Usage: $0 {start|stop|restart}"
esac
exit 0
{% endhighlight %}
press <strong>ESC </strong>to leave the insert mode and enter <strong>:wq</strong> to save and quit the file.

Change the permission on the file using chmod
<blockquote>sudo chmod 755 tomcat</blockquote>
Add script to start with system services
<blockquote>sudo /sbin/chkconfig --add tomcat

sudo /sbin/chkconfig --level 234 tomcat on</blockquote>
Now the service will start when the server is started. Execute following command to test your scripts.
<blockquote>sudo /sbin/service tomcat stop

sudo /sbin/service tomcat start</blockquote>
And that’s about it for installing tomcat on CentOS

<strong>Important: Once again make sure you replace software versions used in this blog with the ones that you download.</strong>