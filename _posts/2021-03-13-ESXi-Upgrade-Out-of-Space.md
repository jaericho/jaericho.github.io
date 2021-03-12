---
layout: post
title: "ESXi Upgrade Out of Space Error"
date: 2021-03-12 08:00:00 -0600
categories: [Stupid_Bugs]
tags: [ESXi, vmware]
---

You enabled the datastore swap but still getting an out of space error.

The [VMware ESXi Patch Tracker](https://esxi-patches.v-front.de/ESXi-6.7.0.html) is an amazing website. It makes patching non-vcenter connected esxi hosts very simple...except when it comes to vmware bugs.

If you keep getting the Out of Space bug everytime you try to patch 6.7 even though you set the datastore swap and checked your inodes, then you'll probably need to apply the patch manually.

![Datastore Swap dialog](/assets/2021/03/datastore-swap.png "I've already done this!")

[This site](https://www.aligrant.com/web/blog/2019-06-25_vsphere_67_errno_28_no_space_left_on_device__part_2) details the steps for the fix nicely:

1. Navigate to [VMWare's Product Patch](https://my.vmware.com/group/vmware/patch) page and identify the latest patch you want to install.
1. Download the patch, which will be a zip file.
1. Click on one of the bulletin links to be taken to the documentation on the update.
1. Look for the Image Profiles section and take note of the image profile name (e.g. `ESXi-6.7.0-20190604001-standard`).
1. Using your preferred method (Web ui, SCP etc) upload your newly downloaded Zip file to the host you wish to patch.
1. Run the update, but instead of referencing an online depot, reference the Zip file, and use the Profile name you previously discovered in step 4, e.g. `esxcli software profile update -p ESXi-6.7.0-20190604001-standard -d /vmfs/volumes/datastore1/ESXi670-201906002.zip`
1. The update will run as normal, and you'll probably need to reboot the host to complete.

I'm not sure if updates past the lastest can be applied online or need to be done this way.
