---
layout: post
title: "Windows 10: WWAN + Ethernet"
date: 2020-05-27 08:00:00 -0600
categories: [Windows]
tags: [Cellular, Ethernet, registry, Windows 10, WWAN]
---

*Windows 10 v1709 prioritizes Ethernet over WWAN.*

My techs were complaining that they used to be able to browse online to look up information while connected to the machine they were servicing. Their machine connection was over Ethernet and they were trying to use a cellular card (WWAN) in their laptops to get online. But that stopped with Windows 10, and they wanted to go back to Windows 7. *(yeah, that's not happening)*

I [found](https://superuser.com/questions/1322552/windows-10-cellular-with-lan) that starting with v1709 [KB4284822](https://support.microsoft.com/en-us/help/4284822/windows-10-update-kb4284822), Windows 10 will stop using a WWAN connection if it detects an Ethernet connection, even if that Ethernet connection has no accessible internet.

> *Adds a new registry key that prevents access to the Internet using WWAN if a non-routable ethernet is connected. To use this new registry key, add IgnoreNonRoutableEthernet” (Dword) on HKEY_LOCAL_MACHINE\Software\Microsoft\Wcmsvc using regedit, and set it to 1.*

Here is the reg key to fix that:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WcmSvc\IgnoreNonRoutableEthernet=dword:00000001`

I haven't found a Group Policy setting that corresponds to this, but I can use other methods to push this change out.
