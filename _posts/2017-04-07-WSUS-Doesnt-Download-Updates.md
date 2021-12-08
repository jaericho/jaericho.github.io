---
layout: post
title:  "WSUS Doesn’t Download Updates"
date:   2017-04-07 10:00:00 -0600
categories: [Stupid Bugs]
tags: [Windows, WSUS]
---

While rebuilding WSUS (once again), I discovered another snag.

When first configuring WSUS I put in `D:` for the drive to store the updates because the wizard didn’t like `D:\`. Unfortunately, **both are wrong**. From what I read in various posts, the wizard used to default to the largest drive with free space and append \WSUS for a directory. If you just specify “D:”, the updates try to download to D:WsusContent and not D:\WsusContent. (The eventlog shows this.)

[A comment](http://daniyar-tech.blogspot.com/2013/06/wsus-on-windows-2012.html?showComment=1488209979675#c6942681862762526728) on this blog post helped fix it without a reinstall:

`wsusutil movecontent D:\WsusContent D:\WsusContent\movelog2.log -skipcopy`

After a reboot (and waiting, as WSUS isn’t very speedy), the updates started downloading.

For future installs: **don’t specify the just the root of a drive, specify a subdirectory** like `D:\WSUS`.

PS: here’s what the log file says:

```
2017-04-07T21:04:23 Successfully stopped WsusService.
2017-04-07T21:04:23 Beginning content file location change to D:\WsusContent
2017-04-07T21:04:23 Did not copy files due to -skipcopy flag.
2017-04-07T21:04:23 Successfully changed WUS configuration.
2017-04-07T21:04:24 Successfully changed IIS virtual directory path.
2017-04-07T21:04:24 Successfully removed existing local content network shares.
2017-04-07T21:04:24 Successfully created local content network shares.
2017-04-07T21:04:24 Successfully changed registry value for content store directory.
2017-04-07T21:04:24 Successfully changed content file location.
2017-04-07T21:04:25 Successfully started WsusService.
2017-04-07T21:04:25 Content integrity check and repair...
2017-04-07T21:04:25 Initiated content integrity check and repair.
```
