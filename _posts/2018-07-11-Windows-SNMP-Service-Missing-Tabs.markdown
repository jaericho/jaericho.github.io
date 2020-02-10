---
layout: post
title:  "Windows SNMP Service Missing Tabs"
date:   2018-07-11 20:33:36 -0600
categories: [Windows]
tags: [SNMP]
---

If you’re trying to configure SNMP on a server from a remote workstation, make sure you have SNMP installed on the remote workstation or you’ll miss the Agent, Traps, and Security tab on the SNMP service properties.

![snmp](/assets/2018/07/snmp_service_properties.png)

w/o SNMP installed on the remote workstation you can’t fully manage SNMP remotely.

H/T: [thomasmaurer.ch](http://thomasmaurer.ch)
