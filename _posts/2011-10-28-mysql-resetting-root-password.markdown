---
layout: post
title:  "Mysql - Resetting root password"
date:   2011-10-28 13:20:00
categories: MySql
---

Once in a while you want to reset your mysql root password, here is how you can do it.

Stop the MySql service

`sudo /etc/init.d/mysql stop`

Restart MySql in safe mode and skip grant table so that you can login with **root** without any password.

`sudo mysqld_safe --skip-grant-tables &`

Login with **root**

`mysql -u root`

Connect to MySql database

`use mysql;`

Reset the password to a new password

`update user set password=PASSWORD("password") where User='root';`

Flush privileges for changes to take affect

`flush privileges;`

Exit from current MySql connection

`exit`

Stop the MySql service running in safe mode

`sudo /etc/init.d/mysql stop`

Start MySql again

`sudo /etc/init.d/mysql start`

Login with your new password

`mysql -u root -p`