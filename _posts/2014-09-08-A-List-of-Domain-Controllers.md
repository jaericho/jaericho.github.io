---
layout: post
title:  "A List of Domain Controllers"
date:   2014-09-08 08:00:00 -0600
categories: [Windows]
tags: [AD, Domain Controllers]
---

[This blog post](http://use-powershell.blogspot.com/2013/04/find-all-domain-controllers-in-domain.html) had a simple solution for getting a list of domain controllers in Powershell.

```posh
Get-ADDomainController -Filter * | Select-Object name
```

Although for my script I ended up dropping the Select-Object name.

```posh
foreach ($DC in (Get-ADDomainController -Filter *)) {
  $DCName = $DC.Name
  $file = (Get-Item "\\$DCName\netlogon\file.txt").LastWriteTime
  Write-Output("$DCName :: $file")
}
```

I used this as a (very) quick and dirty way to diagnose an AD replication issue by comparing a file's known modify datetime with copies in the other DC's netlogon folder.
