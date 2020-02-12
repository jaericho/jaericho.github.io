---
layout: post
title:  "Global Hotkey for New Email"
date:   2018-06-19 20:33:36 -0600
categories: [Windows]
---

I found how to make a global hotkey shortcut that opens a new email and I’ve found it quite useful.

1. Create a new shortcut on the desktop.
1. Point it to the outlook.exe file.
1. In the Target field append `/c ipm.note` at the end.
1. Select a key for the shortcut field. (I selected “m”, ctrl+alt will be automatically added.)

![new_mail_shortcut](/assets/2018/06/new_mail_shortcut.png)

`"C:\Program Files (x86)\Microsoft Office\Office16\OUTLOOK.EXE" /c ipm.note`

Now I can press Ctrl+Alt+m anywhere and I get a new email window in Outlook.
