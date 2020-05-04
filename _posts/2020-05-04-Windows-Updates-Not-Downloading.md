---
layout: post
title:  "Windows Updates Not Downloading"
date:   2020-05-04 08:00:00 -0600
categories: [Stupid_Bugs]
tags: [0x800706D9, BITS, Error, Firewall, Windows, Windows Update]
---

Updates weren't downloading because the Firewall service was disabled.

I had a Windows 2016 server that would not download updates from the local WSUS server. I restarted wuauserv, restarted BITS, deleted the SoftwareDistribution folder. Everything I could find.

I ran [Get-WindowsUpdateLog](https://docs.microsoft.com/en-us/powershell/module/windowsupdate/get-windowsupdatelog?view=win10-ps) and there were many `0x800706D9` errors in the log:

```
2020/05/04 10:09:52.3104833 1436  7896  DownloadManager BITS job {C1A41E05-EC02-4163-AE4F-60949FCB7FA0} hit a transient error, updateId = {F5D1CD88-3A34-479E-B8AF-B6557C9F92E8}.200 <NULL>, error = 0x800706D9
2020/05/04 10:09:52.3112657 1436  7896  DownloadManager Error 0x800706d9 occurred while downloading update; notifying dependent calls.
```

It looks like an issue with BITS.

This [blog post](http://blog.configmatt.com/2018/06/0x800706d9-there-are-no-more-endpoints.html) helped me find the fix. Turns out the problem was that the Windows Firewall service was disabled. I re-enabled the firewall service (while still leaving the firewall turned off), restarted the Windows Update service, then rechecked for updates.

The updates started downloading immediately.
