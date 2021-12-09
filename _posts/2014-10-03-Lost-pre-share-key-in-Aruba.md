---
layout: post
title: "Lost Pre-Share Key in Aruba"
date: 2014-10-03 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Aruba, InstantOS, PSK, Recovery, Wifi]
---

After taking over several Aruba Instant swarms, I lost the pre-share WPA passkey to a wireless network.

Luckily, in InstantOS I could still see the key unencrypted with this enable mode command:

    sh run no-encrypt

Other blog posts said to use:

    encrypt disable
    sh run

However, that didn’t work for me. That may only be for the full controller.
