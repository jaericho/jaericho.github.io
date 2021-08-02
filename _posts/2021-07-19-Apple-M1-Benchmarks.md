---
layout: post
title: "Apple M1 + Benchmarks"
date: 2021-07-27 08:00:00 -0600
categories: [Hardware]
tags: [Apple, Benchmark, Handbrake, Intel, M1, MacBook Air]
---

After jumping in to [test a Mac]({% post_url 2021-05-14-First-Mac-in-a-long-time %}) for my parents, I finally gave in an bought a new MacBook Air with the [M1 processor](https://infogalactic.com/info/Apple_M1).

I like the keyboard. I'm glad I skipped the butterfly keyboard fiasco, but I'm still trying to overcome muscle memory with ctrl+backspace to delete a whole word. And I miss an actual "delete", and not a renamed backspace to delete. But I do realize that this is a laptop keyboard too.

Sleep/Waking is butter smooth and very reliable. After getting used to an iPad's instant and reliable sleep/waking I really notice the failures on my works Dell laptop when it doesn't work 100% of the time. Or my home-built machine whose sleeping started to cause BSOD's recently.

The whole package is quite slick, and the longer I'm in this sysadmin game, the more I appreciate not having to mess around with my home equipment.

I bought a [second-generation iBook G3](https://en.wikipedia.org/wiki/IBook#iBook_G3_Dual_USB_(%22Snow%22)) almost 20 years ago and I ended up quickly selling it because I had no use for it. Since my home-built gaming rig can't run Windows 11 (no TPM 2.0) and my gaming time has dropped significantly in the past year. I will try and keep this as my daily driver.

Here are some quick and dirty benchmarks of my own workflows for the Apple M1.

### Diablo III

Let's be honest here, the M1 is still integrated graphics, but would it still be playable? In a pinch, maybe, but I doubt it would work for very long. I didn't test any rifts and I'm not going to bother.

| **Apple M1** | **i7-4790k + 1070**
| ~50 fps in town with graphics turned way down. | **100+ fps**

### Factorio

I didn't have a megabase to test [Factorio](https://www.factorio.com), but the biggest base I had was buttery smooth with everything turned up and rendering in native resolution.

| **Apple M1** | **i7-4790k + 1070**
| 60/60 fps/ups | 60/60 fps/ups

### Handbrake 1.4.0

What is so amazing is that I'm using the MacBook Air which is passively cooled and it will thermally throttle itself after a minute or two. I'm really curious as to the [Handbrake](https://handbrake.fr) performance of an actively cooled M1 in the Mac Mini and excited to see what the next gen chip will be like.

|| **Apple M1** | **i7-4790K** | **(2x) E5-2680 v2**
| x264[^1] (480p) | TDB | TDB | TDB
| x265 (1080p) | TDB | TDB | TDB
| x265[^2] (480p) | 28.54 fps (+7.5%) | **30.84 fps** | 23.26 fps (+24.5%)
| x265 (1080p) | 4.69 fps (+37.2%) | 4.59 fps (+38.5%) | **7.47 fps**

(The percentages are the increase in encoding time.)

[![Apple M1 logo](/assets/2021/07/apple-m1-logo.jpg)](https://www.apple.com/newsroom/2020/11/apple-unleashes-m1/)

[^1]: Preset: Super HQ 480p30 Surround No audio or subtitles.
[^2]: Custom preset: x265, 8-bit, slow, crf18, limit-sao:bframes=8:psy-rd=1:aq-mode=3. No audio or subtitles.