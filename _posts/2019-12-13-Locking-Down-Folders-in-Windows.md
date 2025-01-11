---
layout: post
title: "Locking Down Folders in Windows"
date: 2019-12-19 20:33:36 -0600
categories: [Windows]
tags: [File Permissions, ACL]
---

I have a situation where users add files to pre-made folder structure, and sometimes they need to move the files around between the various subfolders.

![Folder Structure](/assets/2019/12/folder-structure.png)

However, the problem begins when users accidentally click’n drag a subfolder into another. Or accidentally click’n drag a LOT of subfolders. They don’t know what they are doing, they are users after all. Problems then compound when the folder structure is replicated with DFS to branch offices.

> Users + trackpad = problems  
> Users + pointing stick = problems²
>
> –Me

Q: How do you lock down the subfolders so the users can’t drag’n drop, move, rename, or delete the subfolders while allowing all file permissions?

A: Add the following ACL to the root folder.

[![Deny Delete ACL](/assets/2019/12/deny-delete-ACL.png)](/assets/2019/12/deny-delete-ACL.png)

This ACL will only apply to the subfolders in the root folder. No drag’n drop, no renaming, no deleting. There is one caveat that users can *create* folders directly under root. However, if they use Windows Explorer they will only be able to create folders called "New Folder", and will not be able to rename them.

The only issue is that I will never know if this is the fix other than never having to restore files in that folder...or maybe I’ll know in a week.

> Do you know who uses TrackPoints and trackballs? Communists.
>
> –Me

UPDATE: Changing the Deny permission from `EVERYONE` to `Domain Users` worked well. I can login to the server with an admin account and manipulate the subfolders while Domain Users are still denied from changing the subfolders. This is fix I was looking for.
