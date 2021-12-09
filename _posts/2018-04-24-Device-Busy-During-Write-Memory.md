---
layout: post
title: "Device Busy During Write Memory"
date: 2018-04-24 20:33:36 -0600
categories: [Cisco]
---

I encountered a scary looking bug today on a router. I tried to save a config and received a “device busy” error. The issue was a stuck vty connection. After clearing it (`clear line vty X`) I could `wr mem` successfully.

[https://supportforums.cisco.com/t5/lan-switching-and-routing/4500x-problem-cannot-write-memory-startup-config-file-open/td-p/2603864](https://supportforums.cisco.com/t5/lan-switching-and-routing/4500x-problem-cannot-write-memory-startup-config-file-open/td-p/2603864)
