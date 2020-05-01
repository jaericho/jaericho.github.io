---
layout: post
title:  "Filter Is Finicky"
date:   2016-11-08 10:00:00 -0600
categories: [Powershell]
tags: [Windows]
---

`Get-ADUser -Filter` is really finicky. I finally figured out what I was doing wrong with the help of this wonderfully detailed [Powershellish.com](http://www.powershellish.com/blog/2015-11-17-ad-filter) post.

Basically, I can’t use properties of variables with `-Filter`

This does NOT work:

```posh
foreach ($user in $userlist) {
  $ADUser = Get-ADUser -Filter{(Surname -eq $user.Surname) -and (GivenName -eq $user.GivenName)}
}
```

This does work:
```posh
foreach ($user in $userlist) {
  $ln = $user.Surname
  $fn = $user.GivenName
  $ADUser = Get-ADUser -Filter{(Surname -eq $ln) -and (GivenName -eq $fn)}
}
```
