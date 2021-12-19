---
layout: post
title: "Plex Needed A Diet"
date: 2021-12-19 08:00:00 -0600
categories: [Software]
tags: [Plex, Space Saving, Thumbnails, Windows]
draft: true
---

After a while, Plex will need to go on a diet.

The default thumbnail generation in Plex is every two seconds and it doesn't much of a library before you're looking at 100+ GB in your Plex installation filled with thumbnails. The thumbnails are nice, but I don't think that one every two seconds is necessary. I read that some client devices will only show thumbnails every 5 seconds, so that seems like a good tradeoff for size but still have accurate thumbnails. I don't think that comment was directed at the AppleTV, so I still don't know what the optimal interval for an AppleTV is.

I changed the setting from 2 seconds to 5 seconds and it really helps save space. It halved my 130+ GB Plex install and I recommend this change to anyone with a moderately sized library.

The instructions can be found [here](https://forums.plex.tv/t/big-media-folder-make-smaller-video-preview-thumbnails/635729/6).

Here were the commands that I used. (Since the Powershell curl command is different than regular curl, I used the Ubuntu distro on the Windows Subsystem for Linux and it worked like a charm.)

First, find out the server token with these [instructions](https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/).

Second, run this command to verify the current setting. It should return `default="2"` and `value="2"` on an unaltered install:

`curl -s "http://<PlexServerIP>:32400/:/prefs?X-Plex-Token=<plextokenhere>" | grep BIFF`

Third, change the value of `GenerateBIFFrameInterval` to "5", for 5 seconds. Change this another number if you'd like something else.

`curl -X PUT "http://<PlexServerIP>:32400/:/prefs?GenerateBIFFrameInterval=5&X-Plex-Token=<plextokenhere>"`

Afterwards, run the first command and you should see: `value="5"`.

This will only affect newly generated thumbnails, so delete all the thumbnails in the library and regenerate them.
