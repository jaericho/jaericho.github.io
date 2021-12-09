---
layout: post
title: "Powershell Beginnings"
date: 2014-08-10 08:00:00 -0600
categories: [Powershell]
tags: []
---

I've never been big on scripting. I taught myself VB.net and made some useful programs, but I've tried several times to get into Powershell and it just hasn't clicked.

However, I finally made a useful script. It gets all the files in a directory recursively. Then iterates over the list and deletes the ones that match a predetermined set of patterns. I kept trying to do this in a clever way, trying to use as few lines as possible and get rid of `IF` statements. Finally said, "Fuck it!" and wrote it my way.

Maybe, that will teach me not to be too clever.

```posh
$FileDeleteList = "dotnetfx*.exe", "jre*.exe", "et_20*.exe", "et 20*.exe", "EDT?Update.*"

# Returns true if the filename matches any of the patterns in the $FileDeleteList
function InFileDeleteList($filename) {
  foreach ($FileDeleteItem in $FileDeleteList) {
    if ($filename -like $FileDeleteItem) {
      return $true
    }
  }
  return $false
}

#Start Here
#Get a list of all the files (recursive and not directories) from the current directory.
$files = Get-ChildItem . -recurse | Where-Object{(!$_.PSIsContainer)}

#Iterate over the files, check if they're in the list, and delete them if they are.
foreach ($file in $files) {
  if (InFileDeleteList($file.Name)) {
    Remove-Item -Force $file.FullName
  }
}
```
