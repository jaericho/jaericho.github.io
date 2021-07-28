---
layout: post
title: "Apple M1 + Benchmarks"
date: 2021-07-27 08:00:00 -0600
categories: [Hardware]
tags: [Apple, Benchmark, Handbrake, Intel, M1, MacBook Air]
---

After jumping in to [test a Mac]({% post_url 2021-05-14-First-Mac-in-a-long-time %}) for my parents, I finally gave in an bought a new MacBook Air with the M1 chip.

I like the keyboard. I'm glad I skipped the butterfly keyboard fiasco, but I'm still trying to overcome muscle memory with ctrl+backspace to delete a whole word. And I miss an actual "delete", and not the renamed backspace to delete.

Sleep/Waking is butter smooth and very reliable. After getting used to an iPad's instant and reliable 'sleeping' and 'waking' I really notice the failures on my works Dell laptop when it doesn't work 100% of the time. Or my home-built machine whose sleeping started to cause BSOD's recently.

The whole package is quite slick, and the longer I'm in this sysadmin game, the more I appreciate not having to mess around with my home equipment.

I bought a white iBook 20 years ago and I ended up quickly selling it because I had no use for it. Since my home-built gaming rig can't run Windows 11 and my gaming time has dropped significantly in the past year. I may keep this as my daily driver.

Here are some quick and dirty benchmarks of my own workflows for the Apple M1.

### Handbrake

|| **Apple M1** | **i7-4790K** | **(2x) E5-2680 v2**
| x265 (480p) | 28.54 fps (+7.5%) | **30.84 fps** | 15.67 fps (+49%)
| x265 (1080p) | **4.69 fps** | 4.59 fps (+2.2%) | TBD

(x265, 8-bit, slow, crf18, limit-sao:bframes=8:psy-rd=1:aq-mode=3)

What is so amazing is that I'm using the MacBook Air which is passively cooled and it will thermally throttle itself after a minute or two. I'm really curious as to the performance of a Mac Mini, an actively cooled M1. 
