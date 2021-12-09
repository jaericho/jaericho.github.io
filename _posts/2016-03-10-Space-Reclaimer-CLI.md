---
layout: post
title: "Space Reclaimer CLI"
date: 2016-03-10 20:33:36 -0600
categories: [Software]
tags: [CLI, Netapp, SnapDrive]
---

`sdcli spacereclaimer start -m <machine> -d <mountpoint> -t <minutes>`

When using it in Task Scheduler put spacereclaimer `start -m <machine> -d <mountpoint> -t <minutes>` in the arguments line, and omit `-m <machine>` to run it on the local machine.

![pic](/assets/2016/03/spacereclaimer_task.png)
