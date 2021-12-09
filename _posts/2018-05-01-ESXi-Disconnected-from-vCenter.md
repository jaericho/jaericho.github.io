---
layout: post
title: "ESXi Disconnected from vCenter"
date: 2018-05-01 20:33:36 -0600
categories: [VMware]
---

One of my esxi 5.5 U3 hosts was disconnected from vCenter. The VMs were still running, but reconnecting it to vCenter would result in an `vmodl.fault.HostCommunication error.`

![vmodl-fault-hostcomm.png](/assets/2018/05/vmodl-fault-hostcomm.png)

I logged into the console and looked at the logs and saw that the ramdisk /tmp was full. I verified that it was full with `esxcli system visorfs ramdisk list` [1](https://communities.vmware.com/thread/472385)

`ls -al /tmp` showed that an error log file was filling up the entire ramdisk. I deleted the file and the host automatically reconnected to vCenter.

![del-log-file](/assets/2018/05/del-log-file.png)
