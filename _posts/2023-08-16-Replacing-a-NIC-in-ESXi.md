---
layout: post
title: "Replacing a NIC in ESXi"
date: 2023-08-16 08:00:00 -0600
categories: [Software]
tags: [ESXi, NIC, VMware, vSphere]
---

*I use cheap Mellanox X-2 cards in my homelab to get 10G*

ESXi 7.0 doesn't support the X-2, so I upgraded to the X-3 and two interesting things stuck out:

1. Despite both cards being single port SFP+ for 10G the X-3 is half the size. *(The heatsink is also smaller. I really should double check the temps.)*
1. ESXi kept all the same IP information and setup when I replaced the X-2. I thinking maybe it was because I put the X-3 into the same PCI-E slot as the X-2. Regardless, that was a very welcome surprise.
