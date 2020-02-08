---
layout: post
title:  "Error While Installing Printer Drivers"
date:   2019-02-10 20:33:36 -0600
categories: [Windows, Stupid Bug]
---

I was having issues installing some HP Universal x64 print drivers. The wizard would fail with an `0x0…57` error. Also `pnputil -e` would fail with an _Enumeration of driver packages failed: Access is denied_ error.

The fix was to login with another admin account, then the drivers installed successfully.