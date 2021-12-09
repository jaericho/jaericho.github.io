---
layout: post
title: "Plex's Skip Intro and a Custom Transcode Directory"
date: 2021-10-01 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Plex, Skip Intro, Transcoding, Windows]
---

Make sure your custom transcoding directory includes the backslash.

I run [Plex](https://plex.tv) in a Windows VM because Windows is easier for me to troubleshoot, and I'm too lazy to switch it to Linux or Docker. Also, I created a [ramdrive](https://www.tenforums.com/tutorials/174094-how-create-ram-disk-imdisk-windows-10-a.html) so I could offload the transcoding directory off of the NAS. It may not help much, but it will keep a little bit of I/O off the NAS since it's now SSDs instead of HDDs.

But after creating the T: drive *(T for "temp", see what I did there?)* and setting the Plex Transcoder temporary directory to `T:` it seemed like everything was working. Weeks later, I found that something had broke the skip intro feature on Plex and I finally put the two together when I found these log entries:

```
ERROR - [Transcoder] T:Transcode\Detection\<guid>: No such file or directory
```

The fix was to add a the backslash: `T:\`

![Plex Transcoder temporary directory setting](/assets/2021/10/plex-transcoder-temp-dir.png)

After that fix, analyzing a season would cause the skip intro feature to scan the files successfully. Perhaps adding a subdirectory and not using the root of a drive might have been a good idea. I've ran into [that issue]({% post_url 2017-04-07-WSUS-Doesnt-Download-Updates %}) before.
