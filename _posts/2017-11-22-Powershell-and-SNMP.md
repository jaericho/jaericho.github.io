---
layout: post
title: "Powershell and SNMP"
date: 2017-11-22 10:00:00 -0600
categories: [Powershell]
tags: [SNMP, Windows]
---

I’ve been trying to get all the snmp on my servers fixed and it’s been kind of a pain. Powershell doesn’t have any good cmdlets, but I’ve found a couple examples. [This](https://sysadminplus.blogspot.com/2017/05/find-all-snmp-settings-of-windows.html) is very nice script, but doesn’t work on remote machines unless you do PS Remoting. (I need to bone up on my PS remoting now.)

I ended up using the following for the base of a script. I need only a very simple script so this looks for a specific registry key which will be the name of the CommunityString. Since mine is ‘Public’, I’m just looking for that.

{% highlight posh %}
function Get-RemoteRegistryValue ([string]$ComputerName, [string]$KeyPath, [string]$Value) {
    try {
        $Hive = [Microsoft.Win32.RegistryHive]::LocalMachine
        $reg = [Microsoft.Win32.RegistryKey]::OpenRemoteBaseKey($Hive, $ComputerName)
        $key = $reg.OpenSubKey($KeyPath)
    } catch {
        return "ERR"
    }
    return $key.GetValue($Value)
}
Get-RemoteRegistryValue -ComputerName $server -KeyPath 'SYSTEM\CurrentControlSet\Services\SNMP\Parameters\ValidCommunities' -Value 'Public'
{% endhighlight %}
