---
layout: post
title: "Flashing Firmware on an LG Blu-ray UHD Drive"
date: 2020-09-18 08:00:00 -0600
categories: [Software]
tags: [Blu-ray, Firmware, MakeMKV, UHD, Upgrade]
---

*MakeMKV is a great program, but the forum guides need some cleanup.*

I bought an LG UHD Blu-ray drive to rip 4K discs, but you have to flash the firmware in order to make it work.

The guides for upgrading firmware on the MakeMKV forums can be really confusing because they have lots of caveats. The flashing process depends on what firmware the drive has, is being flashed to, whether or not the firmware is encrypted.

My drive is an LG WH16NS60 with firmware 1.03. It was made in 2020-06, so the firmware is encrypted.

[This video](https://www.youtube.com/watch?v=jyQV1aPlbow) worked for my drive.

{% include youtube.html id="jyQV1aPlbow" %}

And here is the example and final command I used:

```
makemkvcon64.exe f --all-yes -d <DRIVELETTER>: rawflash enc -i \path\to\firmware.bin

makemkvcon64.exe f --all-yes -d F: rawflash enc -i C:\path\to\firmware\HL-DT-ST-BD-RE_WH16NS60-1.03-NM00600-212005081010.bin
```
