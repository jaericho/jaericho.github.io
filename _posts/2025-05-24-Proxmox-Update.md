---
layout: post
title: "Proxmox Update"
date: 2025-05-24 08:00:00 -0600
categories: [Linux]
tags: [ESXi, LXC, Proxmox, VCSA, VMware, VM]
---

*Broadcom said 'subscribe or suffer', I chose Proxmox and just suffer a little differently now.*

My first encounter with Proxmox was during either the 4.x or 5.x days and it wasn't a good experience. Returning to it during the 8.3+ days has been a much more stable experience. However, there are some important features I miss from VCSA/ESXi: VMFS and host hibernation.

Currently, I have a TrueNAS server hosting my VMs with a simple striped mirror setup across several SSDs. With VCSA/ESXi I presented up an iSCSI lun to the ESXi hosts, formatted it with VMFS and everything worked beautifully. I had live snapshots, good performance, and easy expandibility. In the Proxmox world, if I want live snapshots and don't use local ZFS storage, my options are quite limited. I could enable them by running QEMU's qcow2 format on top of ZFS, but that would be stacking two copy-on-write filesystems and that’s asking for trouble. Since I'm not running a hyperconverged setup and my current system is running well, I'm bummed that I don't have live snapshots anymore.

One solution is to migrate to a hyperconverged setup and repurpose my current TrueNAS server as a Proxmox Backup Server. That should get me live snapshots and a good backup solution, as I currently only have backups for the data and not the VMs.

The second downside of moving to Proxmox was the loss of sleeping one of the hosts when it's not needed. My two hand-me-down servers have plenty of memory, and one host is more than enough to run everything. VMware made it easy: I could put one host to sleep to save power and wake it via VCSA when needed. For upgrades, I’d wake the sleeping host, migrate all VMs to it, upgrade the first host, then move everything back, and sleep the second hosta again. Presto! Zero downtime upgrades.

I can still do the upgrades with no downtime (containers still take an outage, but I'm fine with that), but Proxmox doesn't let me sleep the second host very easily, and I can't wake the host remotely either. I might be able to script something for WoL, but Proxmox clusters don't seem to play nicely when one node is disconnected. I couldn't change a container when the second host was disconnected.

Are these dealbreakers? No. Not since Broadcom started putting updates to VCSA/ESXi behind a subscription. It would become unweildly to keep using VMware.
