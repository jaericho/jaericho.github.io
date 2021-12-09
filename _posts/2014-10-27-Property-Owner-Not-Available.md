---
layout: post
title: "Property Owner Not Available"
date: 2014-10-27 08:00:00 -0600
categories: [Stupid Bugs]
tags: [SQL]
---

I ran across an issue today where I did not have access to the properties on a database.

Even while logged in with administrator I still couldn’t access the properties.

Here was the error: ![Property Owner Not Available](/assets/2014/10/property-owner-not-available.png)

[This blog post](http://blogs.msdn.com/b/suhde/archive/2009/04/05/property-owner-is-not-available-for-database-dbname.aspx) helped in fixing it. Running `sp_helpdb <dbname>` showed that the owner field was `NULL`. Probably because the old dbowner was removed from Security Logins of the SQL Server.

I ran the following and the issue was fixed.

```sql
use <dbname>
go
sp_changedbownder @loginame = 'sa'
go
```

(Although I’m not really sure why Microsoft decided to spell loginame that way.)
