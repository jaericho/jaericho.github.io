---
layout: post
title:  "Cloudflare Doubles Perf of Linux Disk Encryption"
date:   2020-03-25 08:00:00 -0600
categories: [Software]
tags: [CloudFlare, Disk Encryption, Kernel, Linux]
---

I like reading stuff like this.

A [blog post from Cloudflare](https://blog.cloudflare.com/speeding-up-linux-disk-encryption/) about how they doubled the performance of the linux disk encryption subsystem by revisiting some old design decisions that were made back when SSDs weren't common, and schedulers that no longer in the kernel.
