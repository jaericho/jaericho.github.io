---
layout: post
title:  "Ubuntu Wifi"
date:   2016-09-20 10:00:00 -0600
categories: [Stupid_Bugs]
tags: [linux, Ubuntu, wifi]
---

It seems like every time I install Ubuntu I have to fix something.

For my old Inspiron 6400 it’s usually wifi. It uses a Broadcom wifi chip and I found [these instructions](https://ubuntuforums.org/showthread.php?t=1748245&page=5&p=10796508#post10796508) useful in fixing it on Ubuntu 16.04

1. Download the [b43 firmware](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz).
1. Copy the folders b43 and b43legacy into /lib/firmware.
1. Reboot
