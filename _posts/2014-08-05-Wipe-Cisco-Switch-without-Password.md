---
layout: post
title:  "Wipe a Cisco 3560 without the Password"
date:   2014-08-05 08:00:00 -0600
categories: [Hardware]
tags: [Cisco, Switch, Wipe]
---

I had a dozen Cisco 3560 switches I needed to wipe, but I couldn’t give the intern the password to the switches. These steps let the intern wipe the switches quickly and easily.

1. Boot up the switch.
1. Hold the Mode button for a few seconds. The LEDs will blink then go solid.
1. Let go of the button and the switch will reboot with a blank config. The original configs will be renamed and backed up on flash.
1. Skip the Initial Configuration dialog then run the regular commands to wipe the switch.

    Switch# write erase
    Switch# delete flash:vlan.txt.renamed
    Switch# reload

You’re done.
