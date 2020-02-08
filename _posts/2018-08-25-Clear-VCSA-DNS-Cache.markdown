---
layout: post
title:  "Clear VCSA DNS Cache"
date:   2018-08-25 20:33:36 -0600
categories: [vmware]
tags: [DNS, systemd]
---

The command to clear the DNS cache on vCenter Server Appliance is

`systemctl restart dnsmasq`

and not

`systemctl restart systemd–resolved.service`

H/T: [http://florian-casse.fr/clear-dns-cache-on-vcsa-6-5-and-later](http://florian-casse.fr/clear-dns-cache-on-vcsa-6-5-and-later)