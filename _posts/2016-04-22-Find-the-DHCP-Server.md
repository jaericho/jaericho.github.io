---
layout: post
title:  "Find the DHCP Server"
date:   2016-06-05 10:00:00 -0600
categories: [Powershell]
tags: [DHCP, Windows]
---

I had to find the dhcp server, but I can’t find any good method in Powershell. So I’m using Powershell to parse `ipconfig /all`.

{% highlight posh %}
$a = [string](ipconfig /all | findstr /C:"DHCP Server")
if ($a.Length -gt 0) { $dhcpserver = $a.Substring($a.IndexOf("1")) }
{% endhighlight %}

Which will take:

    DHCP Server . . . . . . . . . . . : 10.10.4.2

And give you:

    10.10.4.2
