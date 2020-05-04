---
layout: post
title:  "Kaspersky and Jabber"
date:   2016-03-11 20:33:36 -0600
categories: [Stupid_Bugs]
tags: [Cisco, Jabber, Kaspersky]
---

I’ve run into a nasty bug in the latest Kaspersky Antivirus and it seems to kill any Jabber calls.

After a couple minutes, Jabber won’t be able to make any calls. It's just dead air. I have commented on a couple forum posts but I haven’t found any definitive fix other than uninstalling Kaspersky.

I’m using KES10 (10.2.4.674) with SP1 MR2 on Win8.1 (x64) and Win10 (x64). And I’ve tried several versions of Jabber:

* 10.6.5
* 10.6.7
* 11.5.1
* 11.5.2

It’s really annoying. At least, Windows 7 x86 doesn’t seem to be affected by this bug.

Update 2016-03-14: It looks like it’s related to the Kaspersky Network filter driver `klwfp.sys`. After disabling system protection, renaming that driver, and rebooting, Jabber works after the two minute mark.

Update 2016-04-08: Kaspersky contacted me today. I am currently testing out a new driver for them and it seems to be working. I’ll need to do more testing on Monday, but so far so good. (knock on wood)

Update 2016-04-12: The fix worked and I learned that once you get used to hands-free calling with Jabber it’s **very** difficult to go back to a regular phone.
