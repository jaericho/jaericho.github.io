---
layout: post
title:  "WTF is it with Linux? (Part 2)"
date:   2020-05-12 10:00:00 -0600
categories: [Linux]
tags: [Disk, Ubuntu, vmware]
---

*Why must I remount a second hdd after every reboot?*

[WTF is it with Linux (Part 1)]({% post_url 2015-12-30-WTF-is-it-with-Linux %})

I like to check out every be Long-Term-Support release of Ubuntu. It's the distro that I know the best and I keep wondering if I could ever move my daily driver over to it. And every time I don't get farther than a few hours and I'm heading for the CLI or the forums to fix some issue, error, or dumb UI/UX problem.

The latest issue was with Ubuntu Desktop 20.04. I have an esxi host and I wanted to update my seed box from 19.10 to 20.04 and since I couldn't in-place upgrade without going to the forums to figure out why `do-release-upgrade` didn't work, I decide to blow it away and start fresh.

The install is fine and everything worked out of the box, but the issue was I had to keep remounting the drive after every reboot.

How does this work in Windows:
1. Add a virtual hdd in esx.
2. Open Disk Management.
3. Click thru a pop up box and walk thru one wizard.

How does this work in Ubuntu:
1. Add a virtual hdd in esx.
2. Open Disks.
3. Look for new hdd.
4. Search forums for obscure command to rescan iSCSI bus or Reboot.
5. Open Disks again.
6. Step thru wizard to create partition and format with ext4.
7. Mount the new disk.
8. Create files and folders and get work accomplished.
9. Reboot and the disk is gone.
10. Search for missing disk.
11. Go back to Disks and remount the disk.
12. Search more forums.
13. Change mount options.
14. Finally it works.

It really feels like the Disks utility, like a lot of things in linux distros, was designed with a half measure, especially when it comes to the UI/UX.

* Why not include a refresh button to avoid the reboot or crazy CLI?
* Why not add an entry to `/etc/fstab` **during** the wizard?

These issues are why I think Linux distros (other than Android) will never be a mainstream OS for consumers. Users don't want to go thru this crap. Normal people don't want CLI. Normal people want appliances, or at least GUIs. When I figured out what was going on with the disk all I could think was, *This would have been another call into the Help Desk.*

---

The final fix was to turn off User Session Defaults in the mounting options. I never did find a satisfactory answer as to what the User Session Defaults were, but apparently when it's enabled and the "Mount at system startup" option is checked but greyed out, that does NOT mean that the User Session Defaults include "Mount at system startup".

IMO, the best design would be to match the greyed out options to what the User Session Defaults are, but at the minimum, a better design would be to *hide* all those Mount options if they aren't applied.

![Default options](/assets/2020/05/mount-options-user-session-defaults.png){:border="1px"}
