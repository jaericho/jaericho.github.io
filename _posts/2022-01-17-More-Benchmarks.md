---
layout: post
title: "More M1 Benchmarks"
date: 2022-01-17 08:00:00 -0600
categories: [Hardware]
tags: [Apple, Benchmark, Handbrake, Intel, M1, MacBook Air, x265]
---

*How about that? Slow really does mean slow.*

Looks like x265 Medium can *really* increase the speed of encoding versus the Slow preset. My [previous benchmark]({% post_url 2021-07-19-Apple-M1-Benchmarks %}) had the dual [E5-2680 v2's](https://ark.intel.com/content/www/us/en/ark/products/75277/intel-xeon-processor-e52680-v2-25m-cache-2-80-ghz.html) beating out the [Apple M1](https://infogalactic.com/info/Apple_M1/) by almost 60% on the Slow preset. (7.5 vs. 4.7 fps) However, I was getting tired of long encodes and a high electric bill, so I decided to give the Medium preset a try. I've [read](https://kokomins.wordpress.com/2019/10/10/anime-encoding-guide-for-x265-and-why-to-never-use-flac/) that Medium vs Slow is about a 2 point CRF difference, so I lowered the CRF to 21 and set the preset to Medium and did an encode to see what would happen.

The results are amazing! The file size is about 10% larger, but the encode time is down 60%. For this round of re-encodes, I'll stick with the M1. This 8 core (4 high perf / 4 efficiency core) processor is handily beating out TWO 10 core / 20 thread processors from just 8 years prior.

|| **Apple M1** | **(2x) E5-2680 v2**
| Encoding time | 00:16:04 | 00:41:04
| Average speed | 38.35 fps | 14.99 fps

The source was a 25:39 minute episode.

Encoder: H.265 10-bit (x265), Framerate: Same as source (variable), Constant Quality: 21.00 RF

Video Options: 	Preset: medium, Tune: none, Options: limit-sao:bframes=8:psy-rd=1:aq-mode=3:aq-strength=0.8:deblock=1,1, Profile: auto, Level: auto
