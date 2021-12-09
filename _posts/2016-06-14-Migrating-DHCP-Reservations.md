---
layout: post
title: "Migrating DHCP Reservations"
date: 2016-06-14 10:00:00 -0600
categories: [Windows]
tags: [DHCP]
---

I had to migrate dhcp servers and the export/restore wasn’t working for me.

I read that the export/restore method only works on the same server. I’m migrating from 2008 to 2012R2. However, there is a command-line method to add DHCP reservations in Windows and there is an easy way to get a list of existing reservations:

`netsh dhcp server dump > output.txt`

I could only get this command to run on the local server. Running it remotely didn’t seem to get all the output, but at least it gave me the reservations and I didn’t have to retype them. (Run these commands from an elevated command prompt.)

`dhcp Server \\dhcpserver.domain.com Scope 192.168.1.0 Add reservedip 192.168.1.10 0123456789ab "host.domain.com" "" "DHCP"`

Kudos to this [blog post](http://www.mpking.com/2013/08/using-netsh-to-export-and-import-dhcp.html) for the tips.
