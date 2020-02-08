---
layout: post
title:  "Windows Spotlight Wallpaper"
date:   2017-12-01 15:33:36 -0600
categories: [Windows]
tags: [Wallpaper]
---

Windows Spotlight has some nice wallpaper and I’d like to keep a couple for later use, so here’s the shortest Powershell script I could make to save them to my Pictures directory:

{% highlight posh %}
$src = "$env:LOCALAPPDATA\Packages\Microsoft.Windows.ContentDeliveryManager_cw5n1h2txyewy\LocalState\Assets"
$dest = "$env:USERPROFILE\Pictures\Windows Spotlight"
Get-ChildItem "$src" | where {$_.length -gt "141160"} | foreach {cp "$src\$_" "$dest\$_.jpg"}
{% endhighlight %}

I only copy files greater than 141160 bytes because some files in that directory are not wallpapers and the largest non-wallpaper file is 141160 bytes, so it’s a good starting point.

![wallpaper](/assets/2017/12/windows-spotlight.jpg)