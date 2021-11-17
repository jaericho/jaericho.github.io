---
layout: post
title:  "Detecting if the VPN is Enabled"
date:   2021-09-23 08:00:00 -0600
categories: [Powershell]
tags: [Cisco AnyConnect, Powershell, VPN]
---

How to to detect if a VPN adapter is being used.

Inspired by [this blog post](https://www.harrycaskey.com/detect-vpn-connection-with-powershell/), I made this Powershell one-liner that returns true if AnyConnect is connected:

```posh
[bool](Get-WmiObject -Query "Select NetEnabled from Win32_NetworkAdapter where Name like '%AnyConnect%'").NetEnabled
```

Well, that was embarrassing. There was a bug in my code. (Embarrassing, but not unexpected.) I should test more thoroughly before posting.

Original code:

```posh
# Written By: Harry Caskey (harrycaskey@gmail.com)
# In this example, I used "AnyConnect", "Juniper" or "VPN" as the connection name's, but you can change this to whatever fits your environment.
$vpnCheck = Get-WmiObject -Query "Select Name,NetEnabled from Win32_NetworkAdapter where (Name like '%AnyConnect%' or Name like '%Juniper%' or Name like '%VPN%') and NetEnabled='True'"

# Set this value to Boolean if it returns a value it's true, if it does not return a value it's false.
$vpnCheck = [bool]$vpnCheck

# Check if $vpnCheck is true or false.
if ($vpnCheck) {
    return $vpnCheck
    exit(0)
}
else {
    return $vpnCheck
    exit(1)
}
```
