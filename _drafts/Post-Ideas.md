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

---

# Converting PCKS8 to PCKS1

I have some aruba instant APs that don't like certs using PCKS8. This stackoverflow post pointed me in the right direction.

<https://stackoverflow.com/questions/2957742/how-to-convert-pkcs8-formatted-pem-private-key-to-the-traditional-format>

This was the final command: `openssl rsa -in private-pcks8.pem -out private-pkcs1.pem`
