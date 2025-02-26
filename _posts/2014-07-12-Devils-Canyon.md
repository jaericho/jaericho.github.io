---
layout: post
title: "Devil's Canyon"
date: 2014-07-12 08:00:00 -0600
categories: [Hardware]
tags: [Build, Devil's Canyon, Intel, Gigabyte]
---

Time for a new build.

## The Brains

![Devil's Canyon](/assets/2014/07/devilscanyon.png){:height="300px" align="right"}

The last computer I built for myself was in April 2008. Quad-core processors were just released, and I splurged on the Yorkfield-based [Q9450](http://ark.intel.com/products/33923/Intel-Core2-Quad-Processor-Q9450-12M-Cache-2_66-GHz-1333-MHz-FSB). It was Intel's Core 2 Quad 2.66 Ghz desktop processor with 12MB of L2 cache on a 45nm process. That processor has served me well over the years. It led me through a lot of gaming, video encoding, and virtualization over the years, but now it will serve me as my dedicated Plex server. It's time to upgrade.

Over the past six years, the only performance upgrades I made to that machine were upgrading from an nVidia 9600GT to a 560Ti, and adding an SSD as my Windows drive. That's pretty good amortization if you ask me.

Six years ago I bought the (reasonably) best Intel desktop processor and I'm doing it again. I splurged on a new [Devil's Canyon i7-4790K](http://ark.intel.com/compare/80807,33923). I'm not much of an overclocker, so the 4.0Ghz base clock speed and turbo boost to 4.4Ghz was quite tempting. It nearly doubles the clock speed compared to the Q9450.

Combined with three generations of microarchitecture upgrades, this will make for quite a large performance upgrade. I'm betting on this chip lasting me the next half-decade. And who knows, maybe I'll start overclocking when the half-decade is up and get more out of my purchase.

## The Rock

I paired my new CPU with a [Gigabyte GA-Z97X-UD3H](http://www.gigabyte.com/products/product-page.aspx?pid=4960#ov). The Q9450 was sitting on a [Gigabyte GA-P35-DS3L](http://www.gigabyte.com/products/product-page.aspx?pid=2599#ov).

One of the best things about the DS3L is its solid-state capacitors. After moving to solid-state capacitors, I'll never go back. No more popped capacitors from cheap manufacturers. Reliability is important to me. The P35 board from Gigabyte has been rock solid for me, so when I was picking out a board for the new CPU I wanted to stick with Gigabyte's Ultra Durable series. So far, I'm liking the board. It has a diverse feature set, including M.2 and SATA Express options, and its layout is clean and usable.

The capacitors on the Z97-UD3H are painted black, which gives it a very slick look. Since I built this machine today, we'll have to see how stable the system is, but I'm not worried about it.

## Always Trouble

Windows took a while to install. I ran into some issues with it recognizing my SSD. At first, it saw the drive, but I couldn't delete the existing partitions. The motherboard manual said to add storage drivers during a Windows 8 installation. However, when I tried that, Windows setup wouldn't see my drive at all. After fiddling with the new UEFI options in the BIOS and performing a BIOS upgrade (from F4 to [F7](http://www.gigabyte.com/products/product-page.aspx?pid=4960#bios)), Windows finally recognized the drive and I was able to delete the existing partitions and install on a blank drive.

Gigabyte's Q-Flash utility made it very simple to update the BIOS. I used a laptop to copy the BIOS image to a flash drive, and from within the Q-Flash utility, I could browse to the flash drive and perform the update. I've been out of the loop for a while, using the same machine for six years, but that's the way it should be.

Kudos, Gigabyte!

## Benchmarks

| | **Q9450** | **i7-4790K**
| Cinebench 10 Rendering (Single CPU):   | 3189  | 8561  (2.68x)
| Cinebench 10 Rendering (Multiple CPU): | 11562 | 32857 (2.84x)
| Cinebench 10 Multiprocessor Speedup:   | 3.63  | 3.84

Handbrake 9.9 v6227 x64 (same quality settings)
(fps measurements are approximate)

| Q9450    x264 (4 cores)   | 40fps
| i7-4790K x264 (8 threads) | 175fps
| i7-4790K x264 (QuickSync) | 400fps
