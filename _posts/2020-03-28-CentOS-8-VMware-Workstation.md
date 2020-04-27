---
layout: post
title:  "CentOS 8, VMware Workstation, and Fit Guest Now"
date:   2020-03-28 08:00:00 -0600
categories: [Computers]
tags: [CentOS, Display Drivers, VMware]
---

A vanilla install of CentOS 8 will not fit the display to the screen in VMware Workstation 15.5.2.

[This StackOverflow answer](https://unix.stackexchange.com/a/551240) was helpful.

> `sudo yum install xorg*vm*`
>
> The Packet xorg-x11-drv-vmware is what you need.

I installed the packages, rebooted, and it worked.