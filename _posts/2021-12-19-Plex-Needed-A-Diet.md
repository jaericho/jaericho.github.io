---
layout: post
title: "Plex Needed A Diet"
date: 2021-12-19 08:00:00 -0600
categories: [Software]
tags: [Plex, Space Saving, Thumbnails, Windows]
draft: true
---

It doesn't take much for Plex to need a diet.

The default thumbnail generation in Plex is every two seconds and it doesn't much of a library before you're looking at 100+ GB in your Plex installation filled with thumbnails. The thumbnails are nice, but I don't think that one every two seconds is necessary. I read that some client devices only do thumbnails every 5 seconds any ways but I don't think that comment was directed at the AppleTV, so I still don't know what the optimal interval for the AppleTV is.

However, changed the setting from 2 seconds to 5 seconds really helps save space. It halved my 130+ GB Plex install and I recommend this change to anyone with a large library.

The instructions can be found [here](https://forums.plex.tv/t/big-media-folder-make-smaller-video-preview-thumbnails/635729/6).

Here were the commands that I used. (Since the Powershell curl command is different than regular curl, I used the Ubuntu distro on the Windows Subsystem for Linux and it worked like a charm.)

This command verifies the current setting. It should return `default="2"` and `value="2"` on an unaltered install:

`curl -s "http://192.168.1.15:32400/:/prefs?X-Plex-Token=<plextokenhere>" | grep BIFF`

This command will change the value of the `GenerateBIFFrameInterval` to "5".

`curl -X PUT "http://192.168.1.15:32400/:/prefs?GenerateBIFFrameInterval=5&X-Plex-Token=<plextokenhere>"`

Afterwards, you should see: `value="5"` returned with the first command.

This will only affect newly generated thumbnails, so I had to delete all the thumbnails in the library and regenerate them, but that seemed to work without issues. 
