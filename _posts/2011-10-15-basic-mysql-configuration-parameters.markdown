---
layout: post
title:  "Basic MySQL Configuration Parameters"
date:   2011-10-15 13:20:00
categories: MySql
---

Here we are going to discuss some basic MySQL configuration parameter for tuning MySql

**max\_connection=50**

_max_connection_ defines the maximum number of simultaneous client connections. Default value is set to 100, you can start with a low value like 20 or 50 and increase them as your application grows.

**table\_cache=2048**

_table_cache_ determines how many open file descriptors MySQL will cache, recommended value for table_cache is max_connection * N where N is the maximum number of tables per join in any of the queries you execute plus some additional for temporary tables and files.

**max\_allowed\_packet=16M**

_max_allowed packet_ defines maximum size data packet can be in MySQL. If you have large data dumps being imported or have blob fields which are large this may be raised. The largest possible packet that can be transmitted to or from a MySQL 5.5 server or client is 1GB.

**tmp\_table\_size=64M**

_tmp_table_size_ defines the maximum size a temporary table can be if this size is reached then temporary table will be created as a file and placed on disk instead of handling in memory.

**max\_heap\_table\_size=64M**

_max_heap_table_size_ defines maximum memory table can grow before it is placed on disk.

**query\_cache\_size=32M**

_query_cache_size_ is a variable that defines how much memory is allocated for caching a query, query caching only caches the query and its internal execution methods it does not cache results of the query. Queries that are cached don’t have to be reevaluated by MySQL for execution methods thus increasing the speed of a query.

Keep in mind MySQL query caching is case sensitive so '_select * from employee'_ is not similar to '_SELECT * FROM EMPLOYEE'_ infact be careful about the extra spaces too :-).

**query\_cache\_limit=64M**

_query_cache_limit_ defines how big a query and its execution method can be and remain in the query cache.

**innodb\_buffer\_pool\_size = 16M**

*innodb\_buffer\_pool\_size* defines the amount of memory that is dedicated to caching innodb data and indexes and it should be at least the size of the_ innodb index space_ or larger, more data is indexed in Ram that means less disk access and faster query returns hence increasing the performance.

*innodb\_buffer\_pool\_size* is one the most important variable to improve performance of MySql. We recommend reading this article for better understanding of this variable. [Choosing innodb_buffer_pool_size](http://www.mysqlperformanceblog.com/2007/11/03/choosing-innodb_buffer_pool_size/)

In the next article we'll discuss how to use _tuning-primer_ tool to determine current usage of index, memory etc and adjusting the values as recommended.