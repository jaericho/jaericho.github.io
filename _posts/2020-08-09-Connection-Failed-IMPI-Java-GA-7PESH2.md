---
layout: post
title:  "Connection Failed: IPMI, Java, and a GA-7PESH2"
date:   2020-08-09 08:00:00 -0600
categories: [Software]
tags: [GA-7PESH2, Gigabyte, IPMI, Java]
---

*Default Java security is too high for the Gigabyte GA-7PESH2 IPMI.*

From this helpful [reddit post](https://www.reddit.com/r/JDM_WAAAT/comments/9dlx2b/ga7pesh2_ipmikvm_wont_connect/):

| I know this is oldish but since it is the top result on google for "ga-7pesh2 ipmi kvm" I thought I would contribute my solution: Removing `3DES_EDE_CBC` from the `jdk.tls.disabledAlgorithms` entry in `Program Files/Java/jre1.8.0_201/lib/security/java.security` fixed this for me without the need to downgrade. Obviously this has some sort of security implications, permitting the use of a weak cipher, but in my opinion it is preferable to running a super old version of java. Do at your own risk, etc.

This worked for me, except Brave/Chrome still failed and I had to use IE11.
