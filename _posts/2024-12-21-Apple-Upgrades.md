---
layout: post
title: "macOS Upgrade Mess"
date: 2024-12-21 08:00:00 -0600
categories: [Apple]
tags: [macOS, Catalina]
---

*When Windows' upgrades are easier, you know Apple has messed it up.*

I obtained a 2012 Mac Mini from my boss that had been sitting in a drawer for years and I decided to upgrade it to the latest version of macOS that could run on it which should be Catalina (10.15). However, I've never run across an OS that was more difficult to install. Gentoo would have probably been easier, and it's all because Apple decided to make it difficult.

The Mac Mini was running Yosemite (10.10), but when running in Recovery Mode I couldn't connect to the App Store to do an install of Catalina (10.15). I kept receiving a "403 forbidden" error when trying to log in.

*"Let's make a boot disk"*, I said. Silly me, Apple doesn't make it easy to create a boot disk. It's not like you can run a program to automatically download and format a USB drive. This isn't Microsoft after all. First, you need a Mac but not a new Mac, like my M1 Air, you need an old Mac. Not because you can't create boot disks on new Macs, no, you need an old Mac because you simply can't download the new OS install file from the App Store unless it's compatible with the Mac you're downloading it on.

In the meantime, I might have deleted the Yosemite (10.10) Recovery Mode when I formatted the HDD because I somehow ended up in the Mountain Lion (10.8) Internet Recovery mode after one of the reboots. I'm not sure what I did, but at least now I was able to reinstall Mountain Lion (10.8) and then use my Windows machine to download the Sierra (10.12) installer because Safari v6.5 couldn't display the [Apple support page](https://support.apple.com/en-us/102662) to download Catalina. I will admit that Recovery Mode is very nice when it works.

So now I'm installing Sierra (10.12), and hopefully, in an hour, I'll be able to install Catalina (10.15), the last macOS that will officially run on this Mac Mini.

Everyday, I inch closer and closer to running linux which I'm sure will be just fine because I've had such [great]({% post_url 2015-12-30-WTF-is-it-with-Linux %}) [luck]({% post_url 2020-05-12-WTF-is-it-with-Linux-Part-2 %}) [running]({% post_url 2021-12-17-Flatpak-and-Mounted-Shares-in-Ubuntu %}) that. (/sarcasm)

UPDATE: It turns out that after installing Catalina (10.15) and after re-downloading the Catalina Installer from the App Store, I can follow the [instructions](https://support.apple.com/en-us/101578) and use the terminal to create a boot disk: `sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume`

So, after I don't need a boot disk then I can create one.

Thanks, Apple.

![Catalina logo](/assets/2024/12/macos-catalina-round.png)
