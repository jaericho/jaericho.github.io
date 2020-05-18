---
layout: post
title:  "LVM in a Virtual Environment"
date:   2015-07-01 08:00:00 -0600
categories: [Software]
tags: [Linux, LVM, OwnCloud, Partition, Swap]
---

I have been fighting against my [owncloud](https://owncloud.org) server the past couple of nights.

The drive is too small and I need to grow the disk. Now, I’m used to a Windows environment and this is a pretty simple task:

1. Grow the disk in esxi
2. Open Disk Management
3. Right click, Extend
4. Profit.

Easy-peesy. Even the command line in Windows is fairly straight forward:

1. `diskpart`
2. `list partitions`
3. `select partition #`
4. `extend`

(Online resizing of boot/system partitions arrived with Server 2008.)

Not so much in Ubuntu. Now, I’m also dealing with LVM which adds annoyances and I’m left to wonder, “Why am I even using LVM in a virtual environment?” I’m late to the game figuring this stuff out. I’ve found [other posts](http://techfromthetrenches.org/2011/06/17/lvm-is-not-as-useful-in-a-virtual-server-environment/) that share my sentiment.

I did some mucking around with a desktop version of 15.04. I think my final choice will be to move the swap to a file (which I will name pagefile.sys just to annoy anti-Microsoft fans), then delete the swap partitions. This will allow me to have a single partition and resize it more easily:

1. Grow disk in esx
2. resize the partition with parted*
3. reboot**
4. resize the filesystem with resize2fs*.

I’m not finding anything that says I can get rid of LVM volumes and convert them to a partition scheme. Unfortunately, I’ll probably end up with a rebuild.

*I resized the partition while mounted with parted. It gave me a warning but it did work.

**I read somewhere that I’d need to reboot after resizing the partition if I did that while it’s mounted. I didn’t test to see if it was necessary.

[This page](https://help.ubuntu.com/community/SwapFaq) was very useful for changing between a swap partition and swap file.
