---
layout: post
title:  "If Apple Asks for a Reboot..."
date:   2017-04-01 10:00:00 -0600
categories: [Stupid_Bugs]
tags: [Apple, Pi-Hole]
---

This is what happens if you don’t reboot after an update to iCloud for Windows:

![apple_dns_requests.PNG](/assets/2017/04/apple_dns_requests.png)

You get thousands of dns requests to *-courier.push.apple.com.

![apple_dns_requests2.PNG](/assets/2017/04/apple_dns_requests2.png)

Thanks Apple.
