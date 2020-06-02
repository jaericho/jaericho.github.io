---
layout: post
title:  "Registering Powershell Sessions"
date:   2020-05-29 08:00:00 -0600
categories: [Powershell]
tags: [Microsoft, Powershell, Windows]
---

Invoke-Command was giving me a strange error.

When trying to use `Invoke-Command` against some workstations, I was getting this error message:

> Connecting to remote server X.X.X.X failed with the following error message : The WS-Management service cannot process the request. Cannot find the Microsoft.PowerShell session configuration in the WSMan: drive on the X.X.X.X computer.

[This blog post](https://sysadminplus.blogspot.com/2016/11/the-ws-management-service-cannot.html) helped me fix it.

Basically, the Powershell endpoint was not registered. `Get-PSSessionConfiguration | select name` showed that my workstations only had `microsoft.powershell.workflow` registered.

Running `Register-PSSessionConfiguration -Name Microsoft.powershell` fixed the issue and allowed my `Invoke-Command` to work.

I'm not sure what exactly causes this. The workstations should all be running WMP5.1 but these are in-place upgrades from Windows 7 to Windows 10. Perhaps that had something to do with it.
