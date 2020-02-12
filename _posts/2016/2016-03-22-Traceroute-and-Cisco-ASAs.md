---
layout: post
title:  "Traceroute and Cisco ASA’s"
date:   2016-03-22 10:00:00 -0600
categories: [Networking]
tags: [ASA, Cisco, ICMP, Traceroute]
---

I had a strange error on a new ASA where doing tracert to a host returned the correct number of hops, but always displayed the destination host at each hop. Adding inspect icmp error fixed it right up.

```
policy-map global_policy
 class inspection_default
  inspect icmp error
```

via [Issue with Traceroute with Cisco ASA’s](https://supportforums.cisco.com/discussion/12628436/issue-traceroute-cisco-asas)
