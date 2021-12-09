---
layout: post
title: "Can’t format VMFS5 partition"
date: 2016-06-05 10:00:00 -0600
categories: [VMware]
tags: [ESXi, Partition, vmfs]
---

While trying to add an ssd to my esxi 5.5 server I encountered a bug when it tried to format and add the storage.

```
Error:A specified parameter was not correct.
Vim.Host.DiskPartitionInfo.spec
Error Stack
Call “HostStorageSystem.ComputeDiskPartitionInfo” for object “storageSystem” on ESXi “x.x.x.x.” failed.
```

I found a [blog post](http://blog.infrageeks.com/blog/2014/1/23/cant-format-a-vmfs-5-volume-on-an-existing-disk.html) describing the same issue and found it was the existing partitions that was causing it to fail. But instead of dropping into the CLI to delete the partitions manually and continue, the comments had another idea: Create a VMFS3 partition then upgrade to VMFS5.

I ended up creating a VMFS3 partition, but deleted it instead of upgrading it. Then I created a VMFS5 partition successfully. I don’t care for upgrading filesystems. I always prefer to start fresh.
