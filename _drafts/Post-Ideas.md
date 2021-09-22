---
layout: post
title:  "Post Ideas"
date:   2021-09-21 08:00:00 -0600
categories: [Meta]
tags: [Blog Ideas]
draft: true
---

*Post Ideas*

---

I have an old server that is getting replaced this year, but the management console still uses flash. For this case, I decided to keep a VM with an old version of flash lying around just in case.

1. Download flash from Internet Archive.
	I read that V32.0.0.363 is the last version without the kill switch, so that may work.
	https://archive.org/download/flashplayerarchive/pub/flashplayer/installers/archive/
1. Install Pale Moon http://linux.palemoon.org/
1. Copy `libflashplayer.so` to `/usr/lib/mozilla/plugins` (on Ubuntu 20.04, I had to manually create this dir: `sudo mkdir -p /usr/lib/mozilla/plugins`)
1. Pale Moon should find flash now.

This page might also be of use: https://gist.github.com/KuromeSan/56d8b724c0696b54f9f81994ae3591d1

---

# Deleting Windows.old

How to delete `Windows.old` without running Disk Cleanup.

[From](https://www.ghacks.net/2017/07/12/remove-the-windows-old-folder-manually/):

```cmd
takeown /f c:\Windows.old\* /r /a /d y
cacls c:\Windows.old\*.* /t /grant administrators:f
rmdir /s /q c:\Windows.old
```

---

# Expanding vmware drive error

After recieving and error of "invalid operation for device '0'" I was able to increase the drive size by going back to the old flash based FlexUI of vcenter.

However, I wonder if PowerCLI would have done it too: https://www.reddit.com/r/vmware/comments/b8q9s4/workaround_for_invalid_operation_for_device_0/

---

# Detecting if VPN is being used.

*How to to detect if a VPN adapter is being used.*

https://www.harrycaskey.com/detect-vpn-connection-with-powershell/

Inspired by that site, I made this one-liner returns true if AnyConnect is connected:

```posh
![string]::IsNullOrEmpty((Get-WmiObject -Query "Select Name,NetEnabled from Win32_NetworkAdapter where Name like '%AnyConnect%' and NetEnabled='True'"))
```
