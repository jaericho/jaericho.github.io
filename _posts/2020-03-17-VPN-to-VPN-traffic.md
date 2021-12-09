---
layout: post
title: "VPN to VPN Traffic"
date: 2020-03-17 10:00:00 -0600
categories: [Networking]
tags: [AnyConnect, ASA, Cisco, Firewall, NAT, Networking]
---

`same-security-traffic permit inter-interface` and `same-security-traffic permit intra-interface` are not the same.

Did you spot the difference? While working on getting VPN users to pass traffic between each other I found out that those commands will conflict with each other.

    same-security-traffic permit inter-interface
    same-security-traffic permit intra-interface

I spotted a post that said these commands are required for vpn users to pass traffic between each other:

```
same-security-traffic permit intra-interface

object network AnyConnect_Users
  AnyConnect_subnet

nat (outside,outside) source static AnyConnect_Users AnyConnect_Users destination static AnyConnect_Users AnyConnect_Users
```

I had those commands already, but I also had `same-security-traffic permit inter-interface` enabled, and that was the problem.

Removing `same-security-traffic permit inter-interface` fixed the issue.

![same-security-traffic](/assets/2020/03/same-security-traffic_permit_interface.png)

`same-security-traffic permit inter-interface` is the top checkbox.

`same-security-traffic permit intra-interface` is the middle checkbox.

*Also, I couldn't add the nat statement with ASDM. It would reset after a refresh. I had to use the CLI.*
