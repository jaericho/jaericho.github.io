---
layout: post
title:  "Raw Device Mapping and 3TB Drives"
date:   2014-07-28 08:00:00 -0600
categories: [vmware]
tags: [hdd, esxi, sata, RDM]
---

Raw Device Mapping is actually easy for sata drives in ESXi.

Not as easy as just picking the drive from the GUI, but I guess we can’t have everything. I followed the instructions from this [blog](http://blog.davidwarburton.net/2010/10/25/rdm-mapping-of-local-sata-storage-for-esxi/) and they worked.

I also found that connecting the 3TB drive to an existing machine to do the formatting and partitioning is the best bet. Trying to initialize and partition the disk from the Windows 7 VM failed, and using a USB adapter failed as well. Connecting it directly to the sata ports on my workstation’s motherboard worked well.
