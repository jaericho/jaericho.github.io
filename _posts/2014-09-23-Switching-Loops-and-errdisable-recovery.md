---
layout: post
title:  "Switching Loops and errdisable recovery"
date:   2014-09-23 08:00:00 -0600
categories: [Stupid_Bugs]
tags: [BPDUGuard, Cisco, Spanning-tree, Switching]
---

I had a switching loop the other day. Nasty and annoying business.

It didn't bring the network down, but it was quite disruptive. Our switches had bpduguard enabled and this did prevent the switching loop, but the switches also had some errdisable recovery options enabled as well. So, after the switching loop was detected and the ports disabled to save the network (yay!), the ports were reenabled 60 seconds later, thus causing another loop and causing the ports to be disabled.

The loops existed just long enough to cause an issue then disappear. Like I said...quite annoying.

Here are the errdisable options I removed from our switches:

    no errdisable recovery cause bpduguard
    no errdisable recovery cause link-flap
    no errdisable recovery interval 60

Once I removed the errdisable options the ports stayed in an errdisable state and the loop cleared up. The user was forced to call into the Help Desk and the issue was resolved.

Now I'm brushing up on my Spanning Tree Protocol and I have a couple good things to note:

* `spanning-tree portfast` does not disable STP on that port. This is how bpduguard still functions. You can have portfast on your access ports and still sleep easy at night.
* I'm liking `spanning-tree portfast bpduguard default` much more after this little looping incident. This is a global command and will enable bpduguard on all portfast ports.
