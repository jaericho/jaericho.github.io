---
layout: post
title: "macOS Upgrade Mess"
date: 2024-12-21 08:00:00 -0600
categories: [Apple]
tags: [macOS, Catalina]
---

*When Windows' upgrades are easier, you know Apple has messed it up.*

I obtained a 2012 Mac Mini from my boss that had been sitting in a drawer for years and I decided to upgrade it to the latest version of macOS that could run on it which should be Catalina (10.15). However, I've never run across an OS that was more difficult to install. Gentoo would have probably been easier. And it's all because Apple decided to make it difficult.

The Mac Mini was running Yosemite (10.10), but when running in Recovery Mode I couldn't connect to the App Store to do an install of Catalina (10.15). Some silly "403 forbidden" error when logging in.

"So let's make a bood disk", I said. Silly me, Apple doesn't make it easy to create a boot disk. You need a Mac, and not a new Mac like your M1 Air. Not because you can't create a boot disks on new Macs. No, you need an old Mac because you can't obtain the new OS install file from the App Store unless it's compatible with the Mac you're downloading it on.

In the meantime, I might have deleted the Yosemite (10.10) Recovery Mode when I formatted the HDD because I ended up the Mountain Lion (10.8) Recovery mode the next time I booted up. I'm not sure what I did, but at least now I was able to reinstall Mountain Lion (10.8) and then use a Windows machine to download the Sierra (10.12) installer from [Apple](https://support.apple.com/en-us/102662).

So now, I'm installing Sierra, and hopefully in half an hour I'll be able to install Catalina, the last macOS that will run on this Mac Mini.

Everyday I inch closer and closer to running linux which I'm sure will be fine (sarcasm) because I've had such [great]({% post_url 2015-12-30-WTF-is-it-with-Linux %}) [luck]({% post_url 2015-12-30-WTF-is-it-with-Linux-Part-2 %}) [running](2021-12-17-Flatpak-and-Mounted-Shares-in-Ubuntu) that.
