---
layout: post
title: "Cleverer Powershell"
date: 2014-08-23 08:00:00 -0600
categories: [Powershell]
tags: [Pipeline, Powershell]
---

In my last post about Powershell, I chastised myself for trying to be too clever by trying to pipeline an entire script into one line.

Well, I think I’m starting to get the hang of the pipeline. My old foreach loop was something like this:

```posh
$files = Get-ChildItem . | Where-Object{(!$_.PSIsContainer)}

foreach ($file in $files) {
  if (InFileDeleteList($file.Name)) {
    Remove-Item -Force $file.FullName
  }
}
```

Taking a hint from a [comment](http://www.networknet.nl/apps/wp/published/powershell-delete-files-older-than-x-days) on a blog, the new script is condensed to (mostly) one line:

```posh
# Delete log files older than a month
$files = Get-ChildItem . | Where-Object{$_.Name -like "*.txt" -and $_.LastWriteTime -le [System.DateTime]::Now.AddDays(-30)} | Remove_Item -Force -Whatif
```

I kept trying to put $_ into the Remove-Item cmdlet but I finally realized I didn’t need it at all.
