---
layout: post
title: "CPPM Works Well But..."
date: 2022-04-12 08:00:00 -0600
categories: [Software]
tags: [Aruba, Clearpass, CPPM, Licensing, Customer Support, VMware]
---

*I don't mind CPPM it works well and I've never had major problems, but Aruba, come on...*

## Disk Layouts

Aruba's CPPM uses a single disk partitioned into two halves to install different major versions. This is so it can boot a previous version in case something catastrophic happens. However, the disk of my initial deployment was too small and needed to be expanded. Even though it's a virtual appliance I can't expand the drive and continue. I think it should be using two disks, each with a single partition for easy expandability.

Yes, you should be able to redeploy the appliance easily *(cattle, not pets and all that)*, but it's not \*that\* easy, and a virtual hdd expansion should be more than doable.

## Licensing

Aruba... why even have the CPPM platform license if the client licenses is what is really needed? It took me more than a month to upgrade a CPPM cluster just because Customer Support could not convey to me, "...open a ticket with, *'I need to have a license released for a cluster migration.'*" 

Thanks Aruba /s
