---
layout: post
title: "Resetting a Cisco ASA5506"
date: 2021-04-28 08:00:00 -0600
categories: [Hardware]
tags: [5506, ASA, Cisco, Firmware]
---

*It's been a while since I had to use `rommon`.*

This site has a good [write up](https://www.binaryroyale.com/2013/04/resetting-a-cisco-asa-5510-to-factory-defaults/) on resetting a Cisco ASA. I used it on an ASA5506.

The gist of it:

1. Boot into rommon
1. `confreg` (answer no)
1. `confreg 0x41`
1. `boot`
1. `enable` (blank password)
1. `write erase`
1. `conf t`
1. `config-register 0x01`
1. `exit`
1. `write`
1. `reload`
