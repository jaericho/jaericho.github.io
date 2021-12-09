---
layout: post
title: "Deleting Windows.old"
date: 2021-09-28 08:00:00 -0600
categories: [Software]
tags: [cleanmgr, Disk Cleanup, Microsoft, Windows]
---

Can't/Don't want to install cleanmgr?

How to delete `Windows.old` without running Disk Cleanup.

[From](https://www.ghacks.net/2017/07/12/remove-the-windows-old-folder-manually/):

```cmd
takeown /f c:\Windows.old\* /r /a /d y
cacls c:\Windows.old\*.* /t /grant administrators:f
rmdir /s /q c:\Windows.old
```

Disk Cleanup is still the better route as it seems to get the job done eventually, but this does work, and I've used it several times. However, sometimes I had to run cacls more than once. That was an odd bug.
