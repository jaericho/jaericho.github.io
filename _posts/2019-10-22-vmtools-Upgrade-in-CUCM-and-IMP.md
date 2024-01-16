---
layout: post
title: "vmtools Upgrade in CUCM and IMP"
date: 2019-10-22 20:33:36 -0600
categories: [Cisco, VMware]
tags: [vmware tools]
---

*vmtools has a simple upgrade in Cisco’s CUCM and IM & Presence.*

1. Start the vmtools guest install in interactive mode.
1. `utils os secure permissive`
1. `utils vmtools refresh`
1. (automatic reboot)
1. `utils os secure enforce`

However, if you forget the `utils os secure permissive` command you will receive the following error during bootup and vmtools will not be upgraded: `init: vmware-tools post-stop process terminated with status 1`

[![pic](/assets/2019/10/forgot_to_disable_selinux_cucm.png)](/assets/2019/10/forgot_to_disable_selinux_cucm.png)
