---
layout: post
title: "Service Accounts for Minor Scripts"
date: 2022-01-01 08:00:00 -0600
categories: [Software]
tags: [Active Directory, Passwords, Scripting, Service Accounts, Windows]
---

Sometimes a fresh perspective is needed.

A developer came to me to discuss service accounts. He was trying to do it properly and not reuse service accounts, but this situation was a very small and minor script generated a tiny file and sent it to a single user. It could have been a scheduled batch script on the user's machine, but there would have been problems with that approach as well.

Eventually I found out the true goal, the dev was trying to pull some info from AD, *properly* write the info to a temp file on a network share, then somehow get it to the user. I suggested that he avoid touching the disk entirely. Instead, pull the info from AD, hold it in memory and just email the user. I think the final product wrote a file to the server's temp drive instead of a network share and emailed it to the user. After struggling for four days on this issue, he wrapped it up in an afternoon after my suggestion.

This might be a good axiom for the future: ***Writing to disk is expensive. Skip it as much as possible.***
