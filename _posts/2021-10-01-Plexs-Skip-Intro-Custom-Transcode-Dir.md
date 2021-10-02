---
layout: post
title:  "Plex's Skip Intro and a Custom Transcode Directory"
date:   2021-10-01 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Plex, Skip Intro, Transcoding, Windows]
draft: true
---

*Make sure your custom transcoding directory includes the backslash.*

I run [Plex](https://plex.tv) in a Windows VM. It's easier for me to troubleshoot and I'm too lazy to switch it to linux. But I did create a [ramdrive](https://www.tenforums.com/tutorials/174094-how-create-ram-disk-imdisk-windows-10-a.html) so I could offload the transcoding directory off of the NAS. It may not help much, but it will at least keep a little bit of I/O off the VM datastore since it's now SSD and not HDD.

But after creating the T: drive (for temp, see what I did there?) and setting the Plex Transcoder temporary directory to `T:` it seemed like everything was working. However, I found that something had broke the skip intro feature on Plex. Looking at the logs I found these entries: `ERROR - [Transcoder] T:Transcode\Detection\<guid>: No such file or directory`

The fix was to add a the backslash: `T:\`. After that fix, analyzing a season would cause the skip intro feature to scan the files successfully.

![Plex Transcoder temporary directory setting](assets/2021/10/plex-transcoder-temp-dir.png)

Perhaps, not using the root of a drive might have been a good idea, I've ran into [that issue](2017-04-07-WSUS-Doesnt-Download-Updates.md) before.
