---
layout: post
title:  "vCenter to VCSA Migration"
date:   2018-08-14 20:33:36 -0600
categories: [vmware]
tags: [VCSA, vCenter]
---

I was trying to migrate from a Windows based vCenter 5.5 install to [VCSA](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.vcsa.doc/GUID-223C2821-BD98-4C7A-936B-7DBE96291BA4.html) 6.5 and after encountering several errors trying to run the migration tool I discovered that I could disconnect and remove a host from vCenter and add it to VCSA without interrupting the VMs.

1. Spin up new VCSA and recreate EVC clusters. (Make sure to have a DNS A record for VCSA before spinning it up.)
1. Stop DRS on the vCenter EVC cluster.
1. Enter maintenance mode for a host. (Don’t evacuate VMs)
1. Disconnect host from vCenter.
1. Remove host from vCenter.
1. Add host to new VCSA.

I lost all the historical performance data, but that’s better than trying to fix SSL certs.

![vcenter_migration_err](/assets/2018/08/vcenter_migration_err1.png)