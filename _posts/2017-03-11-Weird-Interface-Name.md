---
layout: post
title: "Weird Interface Name"
date: 2017-03-11 10:00:00 -0600
categories: [Linux]
tags: [eth0, ethernet, systemd, Ubuntu]
---

I didn’t know that systemd was going to screw with the ethernet interface names in 16.04, so it was quite a surprise when I fired up a new install of Ubuntu 16.04.2 LTS and found enp0s3 instead of my trusty old eth0.

[This page](https://major.io/2015/08/21/understanding-systemds-predictable-network-device-names/) has a great write up on why the change was made.

And

[This page](http://www.itzgeek.com/how-tos/mini-howtos/change-default-network-name-ens33-to-old-eth0-on-ubuntu-16-04.html) has a great write up on how to change it back.

I prefer the second link.
