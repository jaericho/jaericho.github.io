---
layout: post
title: "Migrating to Proxmox"
date: 2025-01-01 08:00:00 -0600
categories: [Linux]
tags: [ESXi, LXC, Proxmox, VMware, VM]
---

*New Year. New Hypervisor.*

It's a new year, and I think it's time to migrate off ESXi and onto [Proxmox](https://www.proxmox.com/). With VMware's acquisition by Broadcom and subsequent implosion, and ESXi's [stricter hardware requirements]({% post_url 2023-08-16-Replacing-a-NIC-in-ESXi %}), I don't want to deal with the hassle anymore. It's too bad because I use vSphere at work and [I like the product]({% post_url Replacing a NIC in ESXi %}). [EVC](https://blogs.vmware.com/vsphere/2019/06/enhanced-vmotion-compatibility-evc-explained.html) makes working on my homelab so much easier work with when I can live vMotion between hosts with different CPUs.

However, I have discovered Linux Containers ([LXC](https://en.wikipedia.org/wiki/LXC)), and I'm finding them to be a lot of fun. I had several services, each running in a VM previously, and they'll still be running in a container now. I like how easy it is to set up a container and how quickly they start. Docker still annoys me, but I'm sure it's because I'm not super familiar with it. I think one day I'll probably get there, probably using something like Unraid for the host, but I'll stick with LXC on Proxmox for now.

I've already migrated my [Pi-Hole](https://pi-hole.net/), [Nginx Proxy Manager](https://nginxproxymanager.com/), [Unifi Network Application](https://www.ui.com/download/releases/firmware/), and [Tautulli](https://tautulli.com/) in just a few hours. There are some [community scripts](https://community-scripts.github.io/ProxmoxVE/) to make it easier to install these containers, but I've stuck with manual installs so far, except for Tautulli. The easy Tautulli install uses Snaps, and I read that Snaps might have issues with LXC, and I didn't want to make host-wide config changes to make one service work.

I didn't have good luck with Proxmox back in the v4.x and early v5.x days. I hope that [v8.3](https://pve.proxmox.com/wiki/Roadmap#Proxmox_VE_8.3) fares better, but then again I don't have much choice. It's either Proxmox or [XCP-NG](https://xcp-ng.org/). Any issues I encounter, I'll have to fix-forward.

Up next is trying to figure out the best way to host all this with my separate [TrueNAS](https://www.truenas.com/) server. The eternal question: iSCSI vs NFS.

![Proxmox logo](/assets/2025/01/Proxmox-logo-stacked-white-background-300.png)
