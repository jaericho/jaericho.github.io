---
layout: post
title: "A Clear Explanation of UAC"
date: 2020-04-28 08:00:00 -0600
categories: [Windows]
tags: [Administrator, Security, UAC, Windows]
---

[This](https://serverfault.com/a/749271) is clearest and simplest explanation of what UAC does to admin accounts that I have read.

Kudos to the [author](https://serverfault.com/users/6352/massimo).

> This could be caused by [User Account Control](https://en.wikipedia.org/wiki/User_Account_Control), a feature (hated by many) which makes so that, even if you have administrative rights, you don't actually have them unless you explicitly request them. There are two distinct policies governing UAC behavior (both found in `Computer settings\Windows settings\Security settings\Local policies\Security` options), one for the built-in `Administrator` account, and another one for all other administrative users:
>
> * User Account Control: Admin Approval Mode for the built-in Administrator account (disabled by default)
> * User Account Control: Run all administrators in Admin Approval Mode (enabled by default)
>
> What this means is: by default, the built-in `Administrator` account is not affected by UAC, while all other administrative users are; thus, it's possible for an administrative user (different from the built-it `Administrator`) to not actually have administrative rights, even if it's a member of the `Administrators` group.
