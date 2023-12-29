---
layout: post
title: "Outlook and High Disk Utilization"
date: 2021-03-29 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Microsoft, Outlook, Stupid Bugs, Teams]
---

*You'd think that after 2020, Microsoft Teams would get better TLC.*

I happened to open Task Manager today and I saw >80% utilization. Using Resource Monitor I tracked it down to the OUTLOOK.EXE process. It was re-creating and writing a .db-journal file in the temp directory constantly.

Some quick googling found that this bug has been around since at least 2019. It's caused by the Teams Meeting Add-in to Outlook. Luckily, there was a [Microsoft forum post](https://answers.microsoft.com/en-us/windows/forum/all/microsoft-applications-causing-100-disk-usage/fa63de3f-a229-49c8-807d-8876ac00b158) that was helpful. Or I should say, it provided a *mostly* effective workaround for the issue.

The workaround according to MS Support: remove the Teams Meetings add-in from Outlook **OR** make the offending files READONLY and OUTLOOK.EXE will stop it's abusive disk I/O. */facedesk*

I can still make Teams meetings within Outlook with the fix, but after sending the invite, the invite window hangs open. Not a big deal for me. But I don't know if I want to roll this out to my users.

Here are the steps for the workaround:
1. Open a command prompt as admin.
1. Run: `attrib +r %appdata%\..\local\temp\*.db*`
1. Restart Outlook. (You might have to kill the process.)

This is completely asinine.

Why can't someone look at this? I'd bet it's because they are too busy trying to add more emoji's to Teams.
