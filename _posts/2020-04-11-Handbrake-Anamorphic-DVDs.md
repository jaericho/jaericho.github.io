---
layout: post
title:  "Handbrake and Anamorphic DVDs"
date:   2020-04-11 08:00:00 -0600
categories: [Computers]
tags: [Anamorphic, Aspect Raio, DVD, Encoding, Handbrake, makemkv, mkvtools, Plex, Ripping]
---

Whomever made the early American DVDs for [Midsomer Murders](https://www.imdb.com/title/tt0118401/) should be punished.

I've been trying to put my Midsomer Murders collection on [Plex](https://plex.tv) and I don't understand why some DVDs can be easy to reencode and some aren't. Even within the same tv show, the DVD sets (seasons) are authored differently. The early sets have a squished picture, but thankfully after about set 11 or so, they are fixed.

Some are in 16:9 and some are 16:9 squished into 4:3. Which makes them look like shit. And trying to fix it with [Handbrake](https://www.handbrake.fr) can be a pain.

## Problem

Here is what I'm dealing with: I ripped the DVD's with [MakeMKV](https://www.makemkv.com/). That works great, and it's even better that with DVD's it's free. However, The picture is supposed to be 16:9, but somehow it's stored on the DVD with non-square pixels so it comes out as 4:3. From what I gather this is called Anamorphic video.

![Squished Video](/assets/2020/04/squished-video.png){:border="1px}

## How to fix

This [reddit post](https://www.reddit.com/r/handbrake/comments/5mm47h/how_to_stretch_from_43_to_169/) pointed me in the right direction and showed me that there are two methods to fix this issue.

### Fix 1: Handbrake GUI

From the reddit post:

> The right thing to do, that you can do in the GUI, is:
>
> - Anamorphic loose
> - Keep aspect ratio off
> - Set the PAR value correctly to stretch it out horizontally

But setting the Anamorphic to loose does allow me to set the PAR value. Something must have changed in later versions. I think it's Custom that I want.

### Fix 1a: Handbrake GUI (with a little CLI)

When the Handbrake GUI fix didn't work for me with these particular DVDs, (it has worked with other DVDs) I tried the CLI method listed in the reddit post.

I found the SAR/DAR/PAR on a good DVD and compared it to a bad DVD with `ffmpeg -i <input.mkv>`

Good DVD: `Stream #0:0(eng): Video: mpeg2video (Main), yuv420p(tv, top first), 720x480 [SAR 8:9 DAR 4:3], 7500 kb/s, 29.97 fps, 29.97 tbr, 1k tbn, 59.94 tbc`

Bad DVD: `Stream #0:0(eng): Video: mpeg2video (Main), yuv420p(tv, top first), 720x480 [SAR 32:27 DAR 16:9], SAR 186:157 DAR 279:157, 29.97 fps, 29.97 tbr, 1k tbn, 59.94 tbc`

With a little trial and error, I was able to plug those SAR _(PAR?)_ numbers from the Bad DVD of `186:157` into the Handbrake GUI:

![Handbrake Adjusted PAR](/assets/2020/04/handbrake-adjusted-PAR.png){:border="1px"}

We want to keep the vertical lines (480) and just stretch out the video horozontally, so 480 lines with a 186:157 aspect ratio means 853 horozontal lines.

### Fix 2: mkvtools

This one is actually the easier fix.

1. Open the file with [MKVToolNix-gui](https://mkvtoolnix.download).
1. Select the video stream.
1. On the right hand side, change `Set aspect ratio` to `16/9`.
1. Re-mux the video. 
1. Use Handbrake normally (with Anamorphic set to Auto).

![mkvtools fix](/assets/2020/04/mkvtools-aspect-ratio-fix.png){:border="1px"}
