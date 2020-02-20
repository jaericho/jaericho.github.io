---
layout: post
title:  "Conditional Where-Object"
date:   2020-02-19 09:00:00 -0600
categories: [Powershell]
tags: [scripting, where-object]
---

I discovered that I can add conditions to Where-Object in Powershell.

```posh
param (
    [Parameter(Mandatory = $true)]
    [string]$GroupName,
    [switch]$IncludeDisabledAccounts
)

Get-ADGroupMember $GroupName | Get-ADUser -Properties Displayname, EmailAddress | `

Where-Object {

    if (!($IncludeDisabledAccounts)) {
        $_.Enabled
    } 
    else {
        $_.Enabled -or !($_.Enabled)
    }
} `
| Sort-Object Surname | Select-Object Displayname, SAMAccountName, EmailAddress, Enabled | Format-Table -AutoSize
```

Without the `-IncludeDisabledAccounts` switch the Where-Object is `$_.Enabled`; however, if the switch is omitted the Where-Object becomes `$_.Enabled -or !($_.Enabled)`

Very clever.

I noticed that the Where-Object had curly braces, like `if` and `foreach`'s, so I figured I'd try adding more code inside of them.
