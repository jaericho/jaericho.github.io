---
layout: post
title:  "DFS-R MaxOfflineTimeInDays"
date:   2016-12-09 10:00:00 -0600
categories: [Windows]
tags: [DFS-R, EventID, Microsoft]
---

I had a screwy server that wouldn’t replicate a folder in DFSR because it had past the 60 day limit. I’m not sure why this server was out of date for so long.

> EventID: 4012
> 
> The DFS Replication service stopped replication on the folder with the following local path: {{ "<folder>" | escape }}. This server has been disconnected from other partners for 152 days, which is longer than the time allowed by the MaxOfflineTimeInDays parameter (60). DFS Replication considers the data in this folder to be stale, and this server will not replicate the folder until this error is corrected.
> 
> To resume replication of this folder, use the DFS Management snap-in to remove this server from the replication group, and then add it back to the group. This causes the server to perform an initial synchronization task, which replaces the stale data with fresh data from other members of the replication group.
> 
> Additional Information:
> 
> Error: 9061 (The replicated folder has been offline for too long.)
> 
> Replicated Folder Name: {{ "<folder>" | escape }}
> 
> Replicated Folder ID: A484AB0F-7DAE-4A43-BFC4-59303224FD23
> 
> Replication Group Name: domain\dfsroot\foldername
> 
> Replication Group ID: 201BA6C5-92C9-4FDF-BE2B-C9FDC6869FBD
> 
> Member ID: 9B24A868-4C07-4BBE-AE09-C0D9427C9A24

Following the suggestion in the EventID, I removed the folder completely from DFS Replication and Namespace and let everything sync back up. The event log even said that the Replication member was dropped. However, when I re-added the folder I received the same error message again.

So I changed the MaxOfflineTimeInDays option to 155 days with this command and restarted the DFSR service:

```
wmic.exe /namespace:\\root\microsoftdfs path DfsrMachineConfig set MaxOfflineTimeInDays=155
net stop dfsr && net start dfsr
```

The event log showed that DFS-R started replicating the folder again and everything is back to normal again. Then I changed the MaxOfflineTimeInDays option back to it’s normal 60 days.
