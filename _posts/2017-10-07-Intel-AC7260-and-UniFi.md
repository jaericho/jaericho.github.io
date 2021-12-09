---
layout: post
title: "Intel AC-7260 and UniFi"
date: 2017-10-07 10:00:00 -0600
categories: [Windows]
tags: [Intel, Ubiquiti, WPA2]
---

An Intel AC-7260 (on my Latitude 7440) was stuck at 54Mbps when connecting to my [Ubiquiti AP AC-Lite](https://www.ubnt.com/unifi/unifi-ap-ac-lite/). It’s been a great AP to me and all my other devices connect right up, so the issue must be with the laptop or wifi adapter. I found that the laptop wouldn’t connect at all if I set WPA2 to use AES only which is recommended because TKIP is deprecated.

![wpa2_auto.PNG](/assets/2017/10/wpa2_auto.png "I don’t like reduced performance.")

When transferring large files I’d only get 3.5MBps. Ohfercryinoutloud, a cheap flash drive does better than that!

After messing with settings and drivers for a while, I finally found what was needed to get the AC-7260 to connect to WPA2 with AES/CCMP.

Using the [latest Intel drivers](https://downloadcenter.intel.com/download/26924/Wireless-Intel-PROSet-Wireless-Software-and-Drivers-for-Windows-10?product=75439) (v19.70)

1. Right Click / Status on the wifi adapter while connected to the SSID.
1. Click Wireless Properties.
1. Go to the Security tab and change the Encryption Type to AES.
1. Set AP to use WPA2 with AES/CCMP.

[![wifi_status.PNG](/assets/2017/10/wifi_status.png "Forcing it to use AES for this SSID.")](/assets/2017/10/wifi_status.png)

Next, just make sure you’re on a A band for best performance by either using the Connection tab next to the Security tab or by using the Preferred Band setting in the Advanced tab of the driver.

![xfer_increase.png](/assets/2017/10/xfer_increase.png)

The changes made a difference.
