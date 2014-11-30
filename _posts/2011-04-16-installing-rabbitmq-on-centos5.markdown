---
layout: post
title:  "Installing RabbitMQ on CentOS5"
date:   2011-04-16 11:00:00
categories: linux rabbitmq
---

<strong>Install EPEL</strong>

It is recommended to use distribution's packaged version of Erlang to run the server. This is part of Fedora, and in EPEL for RHEL. To enable EPEL run the following command<strong>
</strong>
<blockquote>su -c 'rpm -Uvh http://download.fedora.redhat.com/pub/epel/5/i386/epel-release-5-4.noarch.rpm'</blockquote>
<strong>Installing Erlang</strong>

Add the package repository provided by the owner of EPEL Erlang
<blockquote>su -c 'wget -O /etc/yum.repos.d/epel-erlang.repo http://repos.fedorapeople.org/repos/peter/erlang/epel-erlang.repo'</blockquote>
<blockquote>yum –y install erlang</blockquote>
<strong>Install RabbitMQ from package manager (Recommended)</strong>
<blockquote>yum -y install rabbitmq-server</blockquote>
<strong>Install RabbitMQ using RPM file</strong>

Download the Fedora RPM version of  rabbitMQ from following link under the section Download the RabbitMQ server.

<a href="http://www.rabbitmq.com/server.html" target="_blank">RabbitMQ</a>
<blockquote>cd /usr/share

sudo wget http://www.rabbitmq.com/releases/rabbitmq-server/v2.4.1/rabbitmq-server-2.4.1-1.noarch.rpm</blockquote>
Execute the downloaded rpm file
<blockquote>sudo rpm -i rabbitmq-server-2.4.1-1.noarch.rpm</blockquote>
<strong>Test the RabbitMQ installation</strong>
<blockquote>sudo  /etc/init.d/rabbitmq-server start

sudo  /etc/init.d/rabbitmq-server status</blockquote>
If you see somewhat following output installation was successful
{% highlight bash %}
Status of node rabbit@xyz ...
[{pid,11519},
{running_applications,[{rabbit,"RabbitMQ","2.4.1"},
{mnesia,"MNESIA  CXC 138 12","4.4.17"},
{os_mon,"CPO  CXC 138 46","2.2.5"},
{sasl,"SASL  CXC 138 11","2.1.9.3"},
{stdlib,"ERTS  CXC 138 10","1.17.3"},
{kernel,"ERTS  CXC 138 10","2.14.3"}]},
{nodes,[{disc,[rabbit@TestServer]}]},
{running_nodes,[rabbit@TestServer]}]
...done.
{% endhighlight %}
You can stop the server by this command
<blockquote>sudo  /etc/init.d/rabbitmq-server stop</blockquote>
<strong>Make RabbitMQ as a service to start at boot</strong>
<blockquote>sudo /sbin/chkconfig rabbitmq-server on</blockquote>
You can use following commands to control rabbitmq service
{% highlight bash %}
sudo /sbin/service rabbitmq-server start
sudo /sbin/service rabbitmq-server status
sudo /sbin/service rabbitmq-server stop
{% endhighlight %}
Enjoy the Rabbit!!