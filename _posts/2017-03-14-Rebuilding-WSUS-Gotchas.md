---
layout: post
title:  "Rebuilding WSUS Gotchas"
date:   2017-03-14 10:00:00 -0600
categories: [Stupid Bugs]
tags: [Windows, WSUS]
---

I had to rebuild my SUS server because the old one was still on Win2008 (x86).

After rebuilding the server, everything is going great. The service is installed, the updates are downloading, and I see that there are updates for the SUS server pending, so I apply them and reboot.

And the updates breaks SUS and the SUS Console giving me a constant “Reset Server Node” error.

I found [this post](https://social.technet.microsoft.com/Forums/systemcenter/en-US/a3ef8e7b-1323-486e-bbdb-a1ce9f705f72/wsus-constant-reset-server-node-errors?forum=winserverwsus) with details to fix it. `KB3159706` needs some post install steps done to unbreak SUS. (Why can’t these post install steps can’t be done automatically or with a warning?)

Summary of the fix:
1. Open an elevated Command Prompt window and run: `"C:\Program Files\Update Services\Tools\wsusutil.exe" postinstall /servicing`
2. Install `HTTP Activation` under `.NET Framework 4.5 Features`
3. Restart the WSUS service.
4. Also, don’t forget to add the port (8530) to the Group Policy:

![gpo_update_settings.PNG](/assets/2017/03/gpo_update_settings.png)

(I haven’t configured SSL yet. It is recommended and it does change the port to 8531.)
