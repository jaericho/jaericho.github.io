---
layout: post
title:  "RunOnce a Powershell Script"
date:   2018-12-26 20:33:36 -0600
categories: [Powershell]
---

Why does it always seems like the most simple of tasks are the most difficult to accomplish?

Goal: run a powershell script on the next login with the RunOnce registry key.

Better idea: bang head against the wall for an hour.

This Stack Overflow page was useful with getting started, but the issue was I couldn’t get the script to be triggered. I’d get a crazy error about the script not having a .ps1 file extension, despite the fact that it clearly did. I thought I tried everything:

* &
* -File
* -Command
* single quotes
* double quotes
* kitchen sink

Doesn’t work:

{% highlight posh %}
C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe -WindowStyle Hidden -NoExit -NoProfile -ExecutionPolicy Bypass -Command ' & \server\share\script.ps1'
{% endhighlight %}

Finally, the only thing that worked was removing all of the “-File” and “-Command” and just passing the file after the Powershell .exe:

Works?

{% highlight posh %}
C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe -WindowStyle Hidden -NoExit -NoProfile -ExecutionPolicy Bypass \\server\share\script.ps1
{% endhighlight %}