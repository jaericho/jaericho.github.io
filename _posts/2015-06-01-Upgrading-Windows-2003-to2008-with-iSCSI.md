---
layout: post
title: "Upgrading Windows 2003 to 2008 with iSCSI"
date: 2015-06-11 20:33:36 -0600
categories: [Software]
tags: [iSCSI, Netapp, Snapdrive, Windows]
---

I know what you are going to say about upgrading Windows in place but sometimes it needs to be done.

I have many 2003 servers that will get an in place upgrade to 2008 and several use Netapp’s Snapdrive to connect to iSCSI LUNs. The iSCSI initiator had to be install separately in 2003 and it’s baked into 2008 out of the box, so it’s best to disconnect the iSCSI drives and uninstall the initiator from 2003 before doing the upgrade.

After the upgrade, start the iSCSI service in 2008, fire up Snapdrive and connect to the LUNs. (After setting your IP to a static address. Sometimes I forget that part.)
