---
layout: post
title:  "Cisco Jabber Lag"
date:   2015-05-15 20:33:36 -0600
categories: [Stupid_Bugs]
tags: [Cisco, Jabber]
---

I noticed that my Cisco Jabber became very laggy when typing and sending chat messages.

A little google-fu found [this page](https://tools.cisco.com/quickview/bug/CSCuu02593) from Cisco. Apparently Microsoft’s `KB3038314` is the cause of it.

I uninstalled the KB and Jabber is back to it’s snappy self. I’m running the latest version of Jabber (10.6.3) and I hope that Cisco can get around this in the next version.

Update: It looks like the lag is fixed in v10.6.4 build 63238.
