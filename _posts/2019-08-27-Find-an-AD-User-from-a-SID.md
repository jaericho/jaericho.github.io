---
layout: post
title:  "Find an AD User from a SID"
date:   2019-08-27 20:33:36 -0600
categories: [Powershell]
tags: [Active Directory]
---

How to find an Active Directory user from a SID:

```posh
get-aduser -Properties SID | where { $_.SID -eq "S-1-5-21-1111111111-222222222-3333333333-44444" }
```
