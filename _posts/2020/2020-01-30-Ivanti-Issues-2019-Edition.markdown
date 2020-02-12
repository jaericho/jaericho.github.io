---
layout: post
title:  "Ivanti Issues: 2019 Edition"
date:   2020-01-30 20:33:36 -0600
categories: [Stupid Bugs]
tags: [Ivanti, Landesk]
---

It’s time for another list of stupid bugs in Ivanti Endpoint Manager (Landesk).

The 2019 Edition of this list deals with my recent upgrade from 2018.3 SU3 to 2019.1 SU2. This version has been out for 6+ months, let’s see what bugs are still there…

* Running wscfg32.exe to upgrade the agent removes Bitdefender and won’t reinstall it because of the ldavbd.dll issue. (We’ve seen this bug in previous versions so it gets top billing today!)*
* PXE service doesn’t stay running, even with only one machine being the PXE rep agent.*
* ~~Agent install will repeatedly prompt for reboot. It looks like a PendingFileRenameOperation reg issue, but deleting the key doesn’t fix it.~~ This was fixed by changing the reboot options for the agent install.
* Removing AV with a Console task, doesn’t always remove the AV.*
* Installing AV with “Interactive Mode” doesn’t do anything.

I’ve decided to be nice and not include the list of annoyances with the list of bugs. These aren’t show stoppers, but they ma
ke you wonder if anyone really thought out these features before rolling them out.

* View Services in Diagnostics doesn’t highlight Ivanti services unlike View Processes that will highlight Ivanti processes.
* View Services in Diagnostics doesn’t default sort by DisplayName like services.msc, so Ivanti services aren’t grouped toget
her.
* View Processes doesn’t highlight Bitdefender procs. More half-assery. If you’re going to adopt someone else’s software, go 
all the way.
* Can’t click on buttons in Diagnostics unless a task is highlighted. Even if buttons aren’t task related. (View Procs)
* The Console doesn’t let Jabber take focus with handset buttons.*
* The Console still get’s stuck on one window when trying to maximize it.*

(*These are recurring bugs from earlier versions.)

I have been running 2019.1 SU2 for less than 2 weeks. I’m sure I’ll find more.
