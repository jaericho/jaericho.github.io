---
layout: post
title: "VCSA Certificate Expiration"
date: 2020-08-07 08:00:00 -0600
categories: [Stupid Bugs]
tags: [Certificates, vCenter, VCSA, VMware]
---

*When certs go bad...*

I woke up this morning to failed backups and unable to login to the vCenter Service Appliance. I eventually discovered it was from expired certificates.

[![VMware warning about expired STS cert](/assets/2020/08/vmware-STS-warning.png)](/assets/2020/08/vmware-STS-warning.png)

*STS expiry will occur without warning and will result in an inability to log in to vCenter.*

Well, maybe we \*should\* get warnings, eh VMware?

The fixes weren't the nicest either:

1. Copy in a python script from a [KB article](https://kb.vmware.com/s/article/79248) to find out if the STS cert is expired.
1. Copy in a bash script from a [KB article](https://kb.vmware.com/s/article/76719) to fix the STS cert.
1. [Regenerate](https://kb.vmware.com/s/article/2112283) all the certs in the box because half of them have expired.

Luckily my environment is pretty simple and we only have one VCSA.
