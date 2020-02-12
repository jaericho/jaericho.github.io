---
layout: post
title:  "Moving DB server for WSUS 3.0"
date:   2015-07-29 08:00:00 -0600
categories: [Windows]
tags: [Database, WSUS]
---

I used [this article](http://www.bonusbits.com/wiki/HowTo:Move_WSUS_Database_to_Another_Server) to move a WSUS db from one SQL Server to another.

The only issue I had was creating the login account for `domain\sus_server$`. When I tried to add the account via the GUI I didn’t have the option to add a domain machine account. I ended up scripting out the original user in the old sql server and running that script on the new sql server. After that, change the registry key on the SUS server to point to the new server and it worked like a charm.

Summary:

1. Stop the SUS services `net stop W3SVC && net stop wuauserv && net stop WsusService`
2. Detach the SUSDB from the current location.
3. Copy the files to the new server.
4. Attach the SUSDB db on the new SQL server.
5. Add `domain\sus_server$` SQL account if missing.
6. Edit the registry of the SUS server to point to the new SQL Server: `HKLM\SOFTWARE\Microsoft\UpdateServices\Server\Setup\SqlServerName`
7. Start the SUS services: `net start W3SVC && net start wuauserv && net start WsusService`
8. Test.
9. Drink beer. (New favorite: [Deschutes Fresh Squeezed](http://www.deschutesbrewery.com/brew/fresh-squeezed-ipa))
