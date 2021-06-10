---
layout: post
title:  "Realtek and ESXi"
date:   2014-07-15 08:00:00 -0600
categories: [VMware]
tags: [NIC, Realtek, vSphere]
---

vSphere 5.5 doesn’t include some Realtek NIC drivers.

While building up an ESXi whitebox from some older hardware, I discovered that vSphere 5.5 doesn’t include some Realtek NIC drivers.

The motherboard is a Gigabyte P35-DS3L and has a Realtek chipset on the NIC. I used the instructions here to take the 8186 chipset drivers (.vib file) from vSphere 5, the 5.5 .iso, and a utility called ESXi-Customizer to slipstream the two to create a custom .iso.

I saved some cash as I didn’t have to buy an Intel based NIC. Although, I probably should get and Intel based NIC and be done with it. There may be a chance that patching the 5.5 install may remove the custom drivers.
