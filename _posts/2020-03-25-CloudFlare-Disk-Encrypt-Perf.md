---
layout: post
title: "Cloudflare Doubles Perf of Linux Disk Encryption"
date: 2020-03-25 08:00:00 -0600
categories: [Software]
tags: [CloudFlare, Disk Encryption, Kernel, Linux]
---

*I like reading stuff like this.*

A [blog post from Cloudflare](https://blog.cloudflare.com/speeding-up-linux-disk-encryption/) about how they doubled the performance of the linux disk encryption subsystem by revisiting some old design decisions made back when SSD's weren't common and the kernel relied on schedulers that no longer exist.
