---
layout: post
title:  "MySql Tuning with indexes"
date:   2011-04-30 13:20:00
categories: mysql
---

This blogs explains how you can improve the performance of your select queries by properly using indexes.

Consider the following query on a data base with no indexes.
> select ci.Name, co.Name, cl.Language from city ci, country co, countrylanguage cl where ci.CountryCode=co.Code and cl.CountryCode=co.code and ci.CountryCode = 'USA';

Lets do an explain on the above query.

> explain ci.Name, co.Name, cl.Language from city ci, country co, countrylanguage cl where ci.CountryCode=co.Code and cl.CountryCode=co.code and ci.CountryCode = 'USA';
Explain command gives out following result

[![](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain11.png "explain1")](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain11.png)

Which means **1004056074** (243*1071*83858) rows had to be examined

Lets add an index to **CountryCode** column of **CountryLanguage** table
> create index idx_CountryCode ON CountryLanguage (CountryCode);
Executing the explain command again gives following result.

[![](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain21.png "explain2")](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain21.png)

Now if you see row scan for CountryLanguage table alone has reduced from **1071** to **12** rows only so in total row scan has been reduced to **14768424**

Now lets add an index on **Code** column of **Country** table
> create index idx_Code ON Country (Code);
Executing the explain command now gives following result.

[![](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain31.png "explain3")](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain31.png)

Now total row scan has been reduced from **14768424** to **46296**

Now we will add index on **CountryCode** column of **City** table.
> create index idx_CountryCode ON City (CountryCode);
Following is the result of explain command.

[![](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain41.png "explain4")](http://blog.hussainanjar.com/wp-content/uploads/2011/04/explain41.png)

Total row scan has been reduced to **3276** rows only which is a lot faster then scanning **1004056074** on non indexed columns.

<span style="text-decoration: underline;">**Things to keep in mind**</span>

Indexs are very powerful but they should be used smartly, creating too many indexes can slow down insert, update and delete process. On which column to add index can be identified by joins in your query, but if a join is with a table which has just 3-4 rows adding index won't help much.
