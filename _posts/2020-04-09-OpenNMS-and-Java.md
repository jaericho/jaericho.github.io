---
layout: post
title:  "OpenNMS and Java"
date:   2020-04-09 08:00:00 -0600
categories: [Stupid Bugs]
tags: [CentOS 8, Java, Linux, OpenNMS]
---

Install OpenNMS on a minimal install on Centos 8. Do not choose Server with a GUI.

Aren't we all supposed to install our servers without GUIs? I love the CLI as much as the next neckbeard, but sometimes it's easier for me to troubleshoot something with a GUI on it. Especially since I'm a Windows admin and I'm not as fluent in Linux as I want to be.

However, when OpenNMS recommends that you install it on a server without a GUI, do it.

I kept running into an error where OpenNMS would start up, but then it would die after a few minutes, and I would see these errors in the log:

```
Mar 30 15:54:55 opennms.localdomain opennms[1679]: Exception in thread "NettyDnsResolver-NIO-Event-Loop-3-3" java.lang.NoClassDefFoundError: io/netty/util/concurrent/DefaultPromise$1
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.concurrent.DefaultPromise.notifyListeners(DefaultPromise.java:421)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.concurrent.DefaultPromise.setValue0(DefaultPromise.java:538)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.concurrent.DefaultPromise.setSuccess0(DefaultPromise.java:527)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.concurrent.DefaultPromise.setSuccess(DefaultPromise.java:90)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.concurrent.SingleThreadEventExecutor$5.run(SingleThreadEventExecutor.java:963)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at io.netty.util.internal.ThreadExecutorMap$2.run(ThreadExecutorMap.java:74)
Mar 30 15:54:55 opennms.localdomain opennms[1679]:         at java.base/java.lang.Thread.run(Thread.java:834)
Mar 30 15:55:04 opennms.localdomain opennms[4801]: Stopping OpenNMS: Trying to stop OpenNMS but it's already stopped.
Mar 30 15:55:04 opennms.localdomain opennms[4801]: [  OK  ]
```

Apparently, when installing Centos 8 with the Server with a GUI option it will install some flavor of java which will conflict with OpenNMS. I didn't mess around with it too much to get the exact cause. But this [post](https://opennms.discourse.group/t/opennms-is-not-starting/295/14) helped me figure it out.

The fix was to reinstall CentOS 8 with GUI-less Server option.

According to the post I could add a minimal Gnome environment and a browser without messing with the OpenNMS install, but I'll try to live without it for now.

I hate Java and it's conflicts.
