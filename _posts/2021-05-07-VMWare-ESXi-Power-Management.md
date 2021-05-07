---
layout: post
title: "VMWare, ESXi, and Power Management"
date: 2021-05-07 08:00:00 -0600
categories: [Hardware]
tags: [BIOS, ESXi, Power Management, VMWare]
---

Just selecting High Performance in the BIOS is not enough.

{% include youtube.html id="e9GWK8Pn8ec" %}

This is a [great video](https://www.youtube.com/watch?v=e9GWK8Pn8ec) about power management within ESXi and here's some things I learned:

Most people think power management is just disabling the cpu from sleeping or going idle, but doing that can prevent any turbo boost from occurring.

From a pure performance standpoint:

* The default BIOS settings from Dell and HP are **terrible**.
* [This screenshot](/assets/2021/05/vmware-dell-power-settings.png) from the video shows the recommended Dell BIOS settings. Darker red is worse. Darker green is better.
* Just selecting max performance in BIOS isn't the best.
* Make sure c-state and p-state are enabled in BIOS.
* Set the BIOS to give power management control to the OS.
* Set ESXi to Balanced performance.

Doing the above steps will let ESX the cpu power management, and with some cores going to idle other cores will be able to turbo boost.

The argument goes something like this: *For most applications (non-latency sensitive apps), using turbo boost with a little latency getting out of idle c-states is more bang for your buck than preventing the latency, with no turbo boost at all.*

I'd love to benchmark this and get numbers (maybe I'll try it at home), but instead I just enabled it in the dev environment. I figure it can only help, even if it's only a little.

Also:

* Certain Virtual Hardware versions can enable/disable cpu instructions, so run that the latest reasonable version.
* EVC can mask some performance too.
