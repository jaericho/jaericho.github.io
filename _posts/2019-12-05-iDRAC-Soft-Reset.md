---
layout: post
title:  "iDRAC Soft Reset"
date:   2019-12-05 20:33:36 -0600
categories: [Stupid_Bugs]
tags: [iDRAC]
---

Today I couldn’t browse to the iDRAC website to one of my servers, but I was able to SSH in and run:

`racadm racreset soft`

After a bit, I saw the iDRAC restart (pings stopped and resumed), and I was able to browse to the iDRAC again.

H/T: [Black Manticore](https://www.blackmanticore.com/bd6a9b2ebe1e6fdd18500e29e192ce8b)
