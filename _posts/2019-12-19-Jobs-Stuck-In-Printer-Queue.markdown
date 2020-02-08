---
layout: post
title:  "Print Jobs Sent to Printer and Stuck in Queue"
date:   2019-12-19 20:33:36 -0600
categories: [Windows]
tags: [Printers]
---
Here’s a funny one.

![Printer Queues](/assets/2019/12/printer-queue.png "Not what I wanted to see in the morning.")

I was updating printer permissions and removed CREATOR OWNER, thinking I didn’t need it. Turns out it is needed.

Without `CREATOR OWNER` (current owner: SYSTEM) with the `Manage Documents` rights, the print jobs would be sent to the printer, print successfully, but would not be removed from the queue. I arrived at work this morning to hundreds of print jobs in the queues.

Adding CREATOR OWNER back to the permissions fixed the issue, and I cleared the queues to remove the jobs already printed.

H/T: [2008-r2-jobs-stay-as-sent-to-printer-if-creator-owner-rights-removed](https://social.technet.microsoft.com/Forums/windows/en-US/6e72268f-4ec2-43a2-9a29-750204b02c3f/2008-r2-jobs-stay-as-sent-to-printer-if-creator-owner-rights-removed?forum=winserverprint)