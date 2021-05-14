---
layout: post
title: "RemoveItem's -Recurse Bug"
date: 2021-03-25 08:00:00 -0600
categories: [Stupid_Bugs]
tags: [Microsoft, RemoveItem, Powershell]
---

tl;dr: There is no solution and it will probably never be fixed.

Why `Remove-Item -Recurse` doesn't work 100% of the time on Windows.

More accurately, I've wondered why Microsoft won't fix it. However, this video shows that file deletes are not synchronous and that delete doesn't really delete. Instead, delete is *mark to delete later*. This is a leftover feature from it's VMX days and was a DOD requirement.

{% include youtube.html id="uhRWMGBjlO8?t=455" %}

This [Github thread](https://github.com/PowerShell/PowerShell/issues/8211#issuecomment-582180714) has a good discussion on it, and it actually asks, *"What does shift+del do that Remove-Item -recurse doesn't?"* which I've wondered for a while.

As far as I understand this, it's not exactly a Powershell issue or bug, and the Powershell team isn't going to waste time to work around it. Especially since it's not an issue on the *nix side, and it looks like this bug may be encountered less frequently in Win10 1909+.

It's still annoying and stupid.
