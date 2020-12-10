---
layout: post
title: "Revisiting x265 Part 2"
date: 2020-12-10 08:00:00 -0600
categories: [Software]
tags: [Encoding, Handbrake, x265]
---

*Deinterlace vs Detelecine. FIGHT!*

First, a hat tip to Kokomins. I've found [his guide](https://kokomins.wordpress.com/2019/10/10/anime-encoding-guide-for-x265-and-why-to-never-use-flac/) for (re)encoding anime to be very useful.

And using that guide, I've settled on using [OPUS](https://infogalactic.com/info/Opus_(audio_format)) for audio now. The Plex app on AppleTV can direct play it and Opus gives high quality at lower bitrate than [Handbrake's](https://handbrake.fr/) AAC implementation. I'm usually doing 96kb for stereo and 384k for 5.1 audio. It's perfectly acceptable to my ears. *And it does seem to be the next new hotness in audio codecs.*

I've been thinking about ripping some of my old anime DVDs and replacing the fansub copies I have on Plex. [Azumanga Daioh](https://www.imdb.com/title/tt0339955/) is a funny series, and the people that did the fansubs did a great job of including cultural notes which makes it a difficult decision to go to a copy without those notes. However, the videos were encoded with [xvid](https://infogalactic.com/info/Xvid) and 640x480 and eventually I wanted a better quality copy.

After ripping all the DVDs, I started to re-encode the episodes but of course I ran into interlacing. Or was it telecine'ing? I decided to do some research on the difference and figure out what I really need to do.

As it turns out the Azumanga Daioh DVDs are telecine'd. And the trick to know is telecine'd video is [3 progressive frames and two interlaced frames](https://forum.videohelp.com/threads/226467-to-interlace-or-deinterlace-that-is-the-question#post1324797).

Azumanga being a newer anime and that it's a slice-of-life show, the DVD source is still quite clean and using x265 with the animation tune, crf 21, and 64k OPUS stereo audio, I was able to squeeze the average episode to less than 100MB.

I'm still having trouble getting some DVDs to deinterlace nicely. The [Bubblegum Crisis Tokyo 2040](https://www.imdb.com/title/tt0175385/) DVDs are a set of them. Detelecine + 23.97 fps seems to get me most of the way there. Deinterlace after that and it cleans up some more, but I can still spot some tough scenes where it's not quite right. Luckily, those are few in number.
