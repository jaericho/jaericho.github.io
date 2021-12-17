---
layout: post
title: "Flatpak and Mounted Shares in Ubuntu"
date: 2021-12-17 08:00:00 -0600
categories: [Linux]
tags: [CLI, Flatpak, Handbrake, Linux, Powershell, Scripting, Ubuntu]
---

Flatpak apps can't access where Ubuntu mounts network shares by default.

This one took me a while to figure out, but I think I understand what is going on. Ubuntu's file explorer mounts SMB shares under `/run/user/1000/gvfs/...`, specifically my handbrake SMB share is mounted under `/run/user/1000/gvfs/smb-share:server=servername,share=handbrake/` and that links to `/home/username/handbrake/`, but Flatpak blacklists access to `/run`. The fix was to mount the network share via the CLI instead of Nautilus.

I ended up mounting the file share via a script I copied from [here](https://askubuntu.com/a/1050499).

`mount -t cifs -o uid=<linuxuser>,username=<serveruser> //<serverip>/handbrake /media/handbrake`

Then I installed `cifs-utils` and made the script executable. I'll just run it before I run my Handbrake scripts.

It was very confusing problem because powershell (my scripting language of choice) could see the files, and the HandbrakeGUI (which is also Flatpak) worked w/o any problems, so all my tests came out successful. I know Ubuntu is all about snaps, not flatpaks, so maybe a different distro would be easier to work with.
