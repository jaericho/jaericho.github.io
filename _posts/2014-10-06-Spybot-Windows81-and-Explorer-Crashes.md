---
layout: post
title:  "Spybot, Windows8.1 and Explorer Crashes"
date:   2014-10-07 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Explorer, Spybot, Windows]
---

I've been fighting an issue where explorer has been crashing on me when ever I'd right-click something in the Navigation pane (the left side tree view).

I would right click on a folder and boom! the window would disappear. I tried to use [ProcMon](http://technet.microsoft.com/en-us/sysinternals/bb896645.aspx) hoping something would stand out to me, but all I could see was a bunch of registry keys and folders with the word `shell` in them before explorer.exe stopped showing up completely.

I knew it had to be an extension because this only happened on right-clicks and it didn't happen when I first installed Windows. So I started uninstalling anything with a right-click menu option. I had uninstalled [Dropbox](http://www.dropbox.com/), [Virtual CloneDrive](http://www.slysoft.com/en/virtual-clonedrive.html), and [7zip](http://www.7-zip.org/) before I stumbled across [Spybot](http://www.safer-networking.org/) (2.4.40). Luckily, Spybot has options to disable the shell integration without uninstalling the entire program. I turned the Windows Explorer integration options off and the problem was gone.

The other thing I found out was the 32bit shell extensions will work, but the 64bit extensions will cause the crash. Very odd as I'm running x64 Windows.

To fix the crashes:

1. Check the Advanced User Mode checkbox on the main window of Spybot.
1. Click Settings.
1. Click the System Integration tab.
1. Click the "Uninstall" button next to the 64bit shell integration option. (I have disabled all the options. I like a clean system tray.)

![pic](/assets/2014/10/spybot_shell_integration.png)
