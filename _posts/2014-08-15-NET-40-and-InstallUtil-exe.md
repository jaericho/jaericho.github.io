---
layout: post
title: ".NET 4.0 and InstallUtil.exe"
date: 2014-08-15 08:00:00 -0600
categories: [Stupid Bugs]
tags: [.NET, InstallUtil]
---

I have a Windows 2003 (x86) server complaining that InstallUtil.exe from .NET 4.0 was not a valid win32 application.

Repairing .NET 4.0 did not help. Reinstalling .NET 4.0 kept causing the x64 version of the file to be installed, not the x86 version. The x64 version is about 40KB. The x86 version is about 28KB.

Replacing the file from a working machine fixed the issue.
