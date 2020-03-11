---
layout: post
title:  "Windows 8 Updates and Audit Mode"
date:   2014-07-22 08:00:00 -0600
categories: [Windows]
tags: [Audit, Microsoft, Windows Update]
---

> Windows update does not function while in Audit mode in Windows 8.1.

That’s a nice little tidbit of information that I would have liked to have known before trying nearly everything I could to troubleshoot why it wasn’t working.

[Chris123NT](http://www.chris123nt.com/2014/02/15/windows-update-in-audit-mode-on-windows-8-1/) has very clear instructions to get around this limitation and apply the updates. I have copied the instructions here. Thank you, Chris123NT.

1. Download the [Windows Update Powershell Module](http://gallery.technet.microsoft.com/scriptcenter/2d191bcd-3308-4edd-9de2-88dff796b0bc)
1. Copy the module folder to `%WINDIR%\System32\WindowsPowerShell\v1.0\Modules`
1. Run PowerShell ISE as Administrator
1. Run the following commands:

```posh
Set-ExecutionPolicy Bypass
Import-Module PSWindowsUpdate
Get-WUInstall
```

The rest should be automated with some prompts.
