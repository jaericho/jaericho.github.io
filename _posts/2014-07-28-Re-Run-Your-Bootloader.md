---
layout: post
title: "Re-Run Your Boot Loader"
date: 2014-07-28 08:00:00 -0600
categories: [Linux]
tags: [boot loader, grub, kernel]
---

While cleaning out some old kernels in the wiki server I built for work, I ran across this suspicious message:

```
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]
```

It made me a little nervous to do a reboot. I’m not sure if anything was broken or would have been trouble, so I didn’t reboot. I found several blog and forum posts that said running the command, sudo update-grub would fix it. After running the command and rebooting, everything is still working.
