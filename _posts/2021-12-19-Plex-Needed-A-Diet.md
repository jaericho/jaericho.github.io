---
layout: post
title: "Plex Needed A Diet"
date: 2021-12-19 08:00:00 -0600
categories: [Software]
tags: [Plex, Space Saving, Thumbnails, Windows]
---

After a while, Plex will need to go on a diet.

The default thumbnail generation in [Plex](https://www.plex.tv) is every two seconds and it doesn't take much of a library before you're looking at a 100+ GB Plex installation filled with thumbnails. The thumbnails are nice, but I don't think that one every two seconds is necessary. I read that some client devices will only show thumbnails every 5 seconds, so that seems like a good tradeoff for size but still have accurate thumbnails. I don't think that comment was directed at the [AppleTV](https://www.apple.com/apple-tv-4k/), so I still don't know what is the optimal interval for an AppleTV.

I changed the setting from 2 seconds to 5 seconds and it really helps save space. It halved my 130+ GB Plex install and I recommend this change to anyone with even a moderately sized library.

The instructions can be found [here](https://forums.plex.tv/t/big-media-folder-make-smaller-video-preview-thumbnails/635729/6).

Here were the commands that I used. (Since the [Powershell version of curl](https://ss64.com/ps/invoke-restmethod.html) has different arguments than Linux's curl, I used the [Ubuntu](https://ubuntu.com/wsl) distribution on the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/) and it worked like a charm.)

First, find out the server token with these [instructions](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/).

Second, run this command to verify the current setting. It should return `default="2"` and `value="2"` on an unaltered install:

```bash
curl -s "http://<PlexServerIP>:32400/:/prefs?X-Plex-Token=<plextokenhere>" | grep BIFF
```

Third, change the value of `GenerateBIFFrameInterval` to "5" for 5 seconds. (or change this to whatever interval you'd like, but I think 5 is a reasonable choice.)

```bash
curl -X PUT "http://<PlexServerIP>:32400/:/prefs?GenerateBIFFrameInterval=5&X-Plex-Token=<plextokenhere>"
```

Afterwards, run the first command and you should see: `value="5"`.

This will only affect newly generated thumbnails, so delete all the thumbnails in the library and regenerate them.

Plex needs to add this as a user option by default.
