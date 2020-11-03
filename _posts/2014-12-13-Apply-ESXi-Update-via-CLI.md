---
layout: post
title:  "Apply ESXi Updates via CLI"
date:   2014-12-23 08:00:00 -0600
categories: [VMware]
tags: [CLI, ESXi, Update]
---

Update 2020-11-03: [This site](https://esxi-patches.v-front.de/ESXi-6.7.0.html) has a lot of great info and links.

Update 2018-08-26: Just run this command from SSH and reboot if you want to upgrade to the latest version. This will also upgrade between major versions, i.e. 6.5 to 6.7.

```
esxcli software vib update -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml
```

With [Mike's excellent post](http://miketabor.com/vmware-vsphere-5-5-update-2-released/), I was able to update my esxi install from Update 1 to Update 2 via the command line.

Summary:
```
esxcli network firewall ruleset set -e true -r httpClient
esxcli software profile update -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml -p ESXi-5.5.0-20140902001-standard
esxcli network firewall ruleset set -e false -r httpClient
reboot
```

To get the list of updates:

```
esxcli software sources profile list -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml
```
