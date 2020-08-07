---
layout: post
title:  "Reclaiming Space on VMs"
date:   2018-01-06 20:33:36 -0600
categories: [VMware]
tags: [unmap, iSCSI, NFS, FreeNAS]
---

Here are some great posts about reclaiming unused space in esxi.

[WHAT’S NEW IN ESXI 6.5 STORAGE PART I: UNMAP](https://www.codyhosterman.com/2016/11/whats-new-in-esxi-6-5-storage-part-i-unmap/)

[IN-GUEST UNMAP FIX IN ESXI 6.5 PART I: WINDOWS](https://www.codyhosterman.com/2017/03/in-guest-unmap-fix-in-esxi-6-5-patch-1/)

[IN-GUEST UNMAP, ENABLEBLOCKDELETE AND VMFS-6](https://www.codyhosterman.com/2017/08/in-guest-unmap-enableblockdelete-and-vmfs-6/)

To get automatic space reclamation you’ll need:

* ESXi 6.5 Update 1
* iSCSI volume formatted with VMFS6. (I think VMFS5 works but there are caveats.)
* Thin provisioned disks.
* Discard option enabled on mount points for your Linux guests.

My new esxi 6.5 host connecting to an iscsi volume on FreeNAS 11.0 works like a charm at least when I force and UNMAP with `sudo fstrim /`

I haven’t had it enabled long enough to watch it work it’s magic, but apparently this means no more filling the drive with zeros, then punching a hole while the machine is offline.

UPDATE 2018-01-20: The magic happens immediately. You can see the updated datastore size immediately after deleting a large file in a linux VM.

It also means that as much as I hate setting up iSCSI I’m not going to go back to NFS if it doesn’t have this.
