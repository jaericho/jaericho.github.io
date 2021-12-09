---
layout: post
title: "Find Public IP from Cisco CLI"
date: 2018-07-17 20:33:36 -0600
categories: [Cisco]
---

Dealing with ISP modems are a pain. I needed to find out the public ip of a dsl modem after it had changed on me. I was hoping [this](https://networkengineering.stackexchange.com/questions/34013/how-to-find-my-public-ip-within-ios) solution would be as simple as it looks and it is.

`more http://ifconfig.me/ip/`

Or if you don’t have DNS configured on the Cisco device:

`more http://153.121.72.212/ip/`
