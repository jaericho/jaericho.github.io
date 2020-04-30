---
layout: post
title:  "ownCloud SMB storage on Ubuntu 16.04"
date:   2019-11-20 20:33:36 -0600
categories: [Linux]
tags: [ownCloud, SMB, Ubuntu]
---

To use ownCloud’s SMB external storage on Ubuntu 16.04 without enabling SMB1, add the following lines to the global section of `/etc/samba/smb.conf`

> client min protocol = SMB2
> 
> client max protocol = SMB3

It looks like Samba on Ubuntu 16.04 (v4.3.11) uses SMB1 by default. (I found this out by enabling SMB1 on my FreeNAS box and everything started working.) Later versions of Samba disable it by default, but they aren’t available on Ubuntu 16.04, and I don’t feel like upgrading to Ubuntu 18.04 today.

![pic](/assets/2019/11/smb-protocol.png)

Just add the lines to the end of the Global section.
