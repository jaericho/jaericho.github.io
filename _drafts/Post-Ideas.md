---
layout: post
title: "Post Ideas"
date: 2021-09-21 08:00:00 -0600
categories: [Meta]
tags: [Blog Ideas]
draft: true
---

*Post Ideas*

---

# Expanding vmware drive error

After receiving and error of "invalid operation for device '0'" I was able to increase the drive size by going back to the old flash based FlexUI of vcenter.

However, I wonder if PowerCLI would have done it too: https://www.reddit.com/r/vmware/comments/b8q9s4/workaround_for_invalid_operation_for_device_0/

---

# Converting PCKS8 to PCKS1

I have some aruba instant APs that don't like certs using PCKS8. This stackoverflow post pointed me in the right direction.

<https://stackoverflow.com/questions/2957742/how-to-convert-pkcs8-formatted-pem-private-key-to-the-traditional-format>

This was the final command: `openssl rsa -in private-pcks8.pem -out private-pkcs1.pem`

---

# CPPM Works Well But...

## Disk Layouts

Aruba's CPPM uses a single disk partitioned into two halves to install different major versions. This is so it can boot a previous version in case something catastrophic happens. However, the disk of my initial deployment was too small and needed to be expanded. Even though it's a virtual appliance I can't expand the drive and continue. I think it should be using two disks, each with a single partition for easy expandability.

Yes, you should be able to redeploy the appliance easily (cattle, not pets and all that), but it's not \*that\* easy, and a virtual hdd expansion should be more than doable.

## Licensing

Aruba... why even have the CPPM platform license if the client licenses is what is really needed? It took me more than a month to upgrade a CPPM cluster just because  I had to sort out licensing and the entire time the answer was, "...open a ticket with, 'I need to have a license released for a cluster migration." 

Complete B.S. Aruba
