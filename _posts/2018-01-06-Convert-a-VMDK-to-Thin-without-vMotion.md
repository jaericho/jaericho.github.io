---
layout: post
title:  "Convert a VMDK to Thin without vMotion"
date:   2018-01-06 15:33:36 -0600
categories: [VMware]
tags: [vMotion, Thin Provision, VMDK]
---

Storage vMotion is wonderful but vMotion isn’t available without vCenter. bah!

[This](https://theitbros.com/convert-thick-provision-lazy-zeroed-disk-to-thin-vmware-esxi/) was a handy guide:

1. Enable SSH to the host.
1. Browse to the VM: `cd /vmfs/volumes/<datastore>/<vm>`
1. Create a thin version of the .vmdk: `vmkfstools -i d <vhdd>.vmdk -d thin <vhdd>-thin.vmdk`
2. Remove the thick .vmdk
3. Attach the thin .vmdk
4. Delete the old .vmdk and *-flat.vmdk
