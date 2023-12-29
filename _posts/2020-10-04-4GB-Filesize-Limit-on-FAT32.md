---
layout: post
title: "4GB Filesize Limit on FAT32"
date: 2020-10-03 08:00:00 -0600
categories: [Stupid Bugs]
tags: [FAT32, Filesystem]
---

*Yet another Quality of Life improvement that Microsoft doesn't add.*

[FAT32](https://infogalactic.com/info/File_Allocation_Table#FAT32) cannot support files over 4GB. If you have a 32GB flash drive, formatted with FAT32, and you try to copy a 14GB .iso to it, you will get the following error.

![File Too large error](/assets/2020/10/file-too-large.png)

Did you catch that? *Too large for the **filesystem***.

* Could Microsoft have a human readable error message? *Yes.*

* Could Microsoft suggest using [NTFS](https://infogalactic.com/info/NTFS) or [exFAT](https://infogalactic.com/info/ExFAT) which don't have a 4GB filesize limitation? *Yes.*

* Could Microsoft do a thousand other little quaility of life improvements that make using Windows easier? *Yes.*

But they don't.
