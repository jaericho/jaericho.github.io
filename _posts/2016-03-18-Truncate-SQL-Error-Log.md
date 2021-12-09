---
layout: post
title: "Truncate SQL Server Error Log"
date: 2016-03-18 10:00:00 -0600
categories: [Software]
tags: [Database, Log, SQL]
---

`sp_cycle_errorlog` is useful.

You can cycle the error log by calling `sp_cycle_errorlog` and then that will close the current error log and cycle the log extensions. Basically, it’ll create a new error log file that SQL Server will be hitting. Then the archived error log(s) can be treated accordingly (delete/move with caution).

This will not technically “truncate” the log, it’ll just roll it over and you can handle the old logs as you so please, like any other file system file.

via [Safe way to truncate SQL Server Error Log – Database Administrators Stack Exchange](http://dba.stackexchange.com/questions/31298/safe-way-to-truncate-sql-server-error-log#31299)
