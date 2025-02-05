---
layout: post
title: "WTF is it with Linux?"
date: 2015-12-30 10:00:00 -0600
categories: [Linux]
tags: [OpenVPN, Ubuntu]
---

The more I work with Linux the more I’m convinced that the problem with the open source model is precisely the opposite of what I would think it would be.

What I think would happen is that the heavy-lifting code—the code that actually does work—would develop slower than the UI/UX code. But what I see happening is that the UI or UX code lags far behind the heavy-lifting code.

My example is OpenVPN. Now, I’m not a complete noob when it comes to Linux. I’m a sysadmin (mostly MS) by trade and while certificates still confuse me at times, I get around well enough. However, installing and configuring OpenVPN on an Ubuntu 14.04 box was beyond a pain in the ass. If it wasn’t for *someone else* writing a tutorial about how to do something *vaguely similar* to what I wanted to accomplish that *mostly fits* the distro I’m using—on top of me being *slightly* familiar with Linux, I never would have been able to get my iPhone VPN'd into my home network.

I’m not trying to do anything out of the ordinary; but in the Linux world, doing mundane tasks means you will still have a fight on your hands. It wouldn’t be sacrilege to put in a couple wizards to help configure OpenVPN in the most common configurations.

I don’t know if developing good UI/UX is tedious and boring or if projects change their methods so often that no one can make decent UI without everything changing underneath them.

I finally got OpenVPN configured and my phone connected up. I used [this tutorial](https://www.howtoforge.com/internet-and-lan-over-vpn-using-openvpn-linux-server-windows-linux-clients-works-for-gaming-and-through-firewalls), and it’s good, but for Ubuntu 14.04, I would recommend adding the following addendum:

> Make your life easier while configuring OpenVPN by doing everything in root (sudo su). I’m not sure why, but the scripts won’t run under regular sudo.

That single tidbit of knowledge would have saved me an hour and a half of my time.
