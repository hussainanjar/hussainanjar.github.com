---
layout: post
title:  "Grails: Cloud Foundry cheat sheet"
date:   2011-10-15 13:20:00
categories: Grails
---

This blog is a cheat sheet for using [Cloud Foundry grails plugin](http://www.grails.org/plugin/cloud-foundry). For details about the commands and how to install plugin please look at the [guide](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/index.html).

#### <span style="text-decoration: underline;">[Deploying Application](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/guide/4%20Deploying%20applications.html)</span>

##### Initial state

grails [cf-apps](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-apps.html) - list of active deployed applications

grails [cf-info](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-info.html) - Details about resources in use (Memory, Services &amp; Apps)

##### Services

grails [cf-services](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-services.html) - display list of available and provisioned services

grails [cf-create-service](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-create-service.html) mysql - Creates an instance of a service

grails [cf-delete-service](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-delete-service.html) mysql-2f5fb76 - Delete an instance of a service

##### Applications

grails prod [cf-push](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-push.html) - Push and optionally start an application

grails prod [cf-push](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-push.html) --services=mysql-2f5fb76 - Push and bind a service

#### [<span style="text-decoration: underline;">Updating applications</span>](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/guide/5%20Updating%20applications%20and%20services.html)

##### Initial state

grails [cf-bind-service](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-bind-service.html) mongodb-eaa5601 - Binds a service to an application.

grails [cf-unbind-service](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-unbind-service.html) mongodb-eaa5601 - Unbinds a service from an application.

##### URLs

grails [cf-map](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-map.html) myotherappname.cloudfoundry.com - Registers an additional URL with the specified application.

grails [cf-unmap](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-unmap.html) myotherappname.cloudfoundry.com - Unregisters a URL from the specified application.

##### Instances

grails [cf-update-instances](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-update-instances.html) 3 - Scale up or down the number of instances.

grails [cf-show-instances](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-show-instances.html) - Displays information about the instances of the specified application.

grails [cf-stats](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-stats.html) - Report resource usage for an application.

##### Memory

grails [cf-update-memory](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-update-memory.html) 1G - Increases or decreases the allocated memory for your application.

##### Start, stop, restart

grails [cf-stop](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-stop.html) - Shuts down the server(s) running the application.

grails [cf-start](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-start.html) - Starts the server(s) for the application. Displays all logs if there's a problem starting.

grails [cf-restart](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-restart.html) - This script is a utility script that calls stop and then start for the specified application.

##### Updating

grails prod [cf-update](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-update.html) - Rebuilds a war file for your application and redeploys it.

grails [cf-delete-app](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-delete-app.html) - Deletes the specified registered application.

grails [cf-delete-all-apps](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-delete-all-apps.html) - Deletes all registered applications.

#### [<span style="text-decoration: underline;">Monitoring</span>](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/guide/6%20Monitoring.html)

##### Crashes

grails [cf-crashes](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-crashes.html) - Displays a brief description of recent application crashes.

grails [cf-crashlogs](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-crashlogs.html) - Displays log files after a crash to help diagnose the cause.

##### Logs

grails [cf-logs](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-logs.html) - Displays log files for an instance to the console, or to a file if specified.

##### Viewing files

grails [cf-list-files](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-list-files.html) / - Lists files in the specified directory on the server.

grails [cf-list-files](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-list-files.html) tomcat

grails [cf-list-files](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-list-files.html) tomcat/webapps

grails [cf-get-file](http://grails-plugins.github.com/grails-cloud-foundry/docs/manual/ref/Scripts/cf-get-file.html) tomcat/webapps/ROOT/css/main.css - Display or download a single file.