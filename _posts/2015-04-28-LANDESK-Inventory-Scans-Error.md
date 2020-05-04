---
layout: post
title:  "LANDesk Inventory Scans"
date:   2015-04-28 20:33:36 -0600
categories: [Stupid_Bugs]
tags: [Inventory Scan, Landesk]
---

I ran into a bugger of a problem with the scans of a freshly imaged host not being accepted by the LANDESK core server.

They kept ending up in the `ErrorBigScan` folder. I finally tracked it down with this KB article, [9.6 Inventory: device is not showing up on 9.6 console after finish installing the agent](https://community.landesk.com/support/docs/DOC-33536)

Turns out, the default max size for an inventory scan is 10MB. The scans of the host were 10.5MB. After I doubled the limit and restarted the inventory service, I took the scans from the ErrorBigScan folder and dropped them back into ldscan and they were eventually imported into the system.

Thank you LANDesk for putting a log in the event viewer saying, “Whoops this scan is too large to be processed.”

(That last sentence was sarcasm.)
