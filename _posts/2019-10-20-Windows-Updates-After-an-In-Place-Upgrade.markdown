---
layout: post
title:  "Windows Update After an In-Place Upgrades"
date:   2019-10-20 20:33:36 -0600
categories: [Windows, Windows Update]
---
Windows Updates taking a crap after an in-place upgrade has to be my biggest gripe about in-place upgrades. But the boss says to do an in-place upgrade so I don’t have much choice.

Looks like these two things might help with Windows Updates just spinning forever after an upgrade.

Stop the Windows Update service and run the commands below:

{% highlight posh %}
cd C:\Windows\System32\wbem\AutoRecover
for /f %s in ('dir /b *.mof *.mfl') do mofcomp %s
{% endhighlight %}

Start the Windows Update service, install [`Windows8.1-KB3102812-x64.msu`](https://www.microsoft.com/en-us/download/details.aspx?id=49544), then reboot.

I am hopeful that this will fix it because `KB2102812` didn’t want to install at first, and after the commands above, it installed immediately. I’m still waiting on confirmation that this will fix the issues because some users can’t wait 2 minutes over lunchtime for me to sneak a reboot in.

I’m not sure how upgrading 2012R2 to 2016 will go, we’ll see in a year or two.

UPDATE 2019-10-21: It looks like `KB2102812` helped. Updates were found and installed after a reboot.