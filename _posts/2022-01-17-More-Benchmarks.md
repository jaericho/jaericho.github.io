---
layout: post
title: "More M1 Benchmarks"
date: 2022-01-17 08:00:00 -0600
categories: [Hardware]
tags: [Apple, Benchmark, Handbrake, Intel, M1, MacBook Air, x265]
---

*How about that? Slow really means slow.*

Looks like x265 Medium can *really* increase the speed of encoding versus the Slow preset. My [previous benchmark]({% post_url 2021-07-19-Apple-M1-Benchmarks %}) had the dual E5-2680v2's beating out the M1 by 30% on the Slow preset. (7.47 vs. 4.69 fps) However, I was getting tired of long encodes and a high electric bill, so I decided to give the Medium preset a try. I've [read](https://kokomins.wordpress.com/2019/10/10/anime-encoding-guide-for-x265-and-why-to-never-use-flac/) that Medium vs Slow is about a 2 point CRF difference, so I lowered the CRF to 21 and set the preset to Medium and did an encode to see what would happen.

The results are amazing! The file size is about 10% larger, but the encode time is down 60%. For this round of re-encodes, I'll stick with the M1.

|| **Apple M1** | **(2x) E5-2680 v2**
| Run time | 00:16:04 | 00:41:04
| Avg speed | 38.35 fps | 14.99 fps

The source was a 25:39 minute episode.

Encoder: H.265 10-bit (x265), Framerate: Same as source (variable), Constant Quality: 21.00 RF

Video Options: 	Preset: medium, Tune: none, Options: limit-sao:bframes=8:psy-rd=1:aq-mode=3:aq-strength=0.8:deblock=1,1, Profile: auto, Level: auto
