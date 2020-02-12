---
layout: post
title:  "Netapp Uploads"
date:   2015-07-09 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Aspera, Netapp, Troubleshooting]
---

Netapp uses a utility called Aspera Connect to upload large log files, core dumps, etc… Aspera Connect uses http or https to transport the data. However it doesn’t use port 80 or 443. Nope, it uses 33001.

Netapp, Aspera, I respectfully suggest you get your heads out of your butts. Use port 80 or 443. Luckily, I’m the firewall guy AND the Netapp guy and I could get around this. If I wasn’t, I would have been taking up more of your tech’s time troubleshooting this issue.

![pic](/assets/2015/07/aspera_connect.png)
