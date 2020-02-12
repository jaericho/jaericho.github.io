---
layout: post
title:  "Migrating ePO Database"
date:   2015-08-01 10:00:00 -0600
categories: [Softare]
tags: [Database, McAfee]
---

While trying to migrate the db for a McAfee ePO server, I ran across these basic instructions:

1. Stop EPO Services
1. Copy the Database and Database LOG Files to the new SQL Server.
1. Attach the Database to the new SQL Server.
1. Configure a user who is dbowner of the EPO Database
1. Start the EPO Tomcat Service only
1. Open [https://epo_server:8443/core/config](https://epo_server:8443/core/config)
1. Change the database settings
1. Restart any EPO server service
1. Check the EPO server Logs if there are any error.

These instructions worked well until I came across step 7 and my Apply button was grayed out and I couldn’t update the db connection settings.

I came across this [knowledge base article](https://kc.mcafee.com/corporate/index?page=content&id=KB82251&ePO0814f) and it said the `db.properties` file was altered and the config page wasn’t parsing the file properly. I found that the db.user.name field was missing. I added it back in and I was able to continue on. Then I rebooted the ePO server and everything was working after that.
