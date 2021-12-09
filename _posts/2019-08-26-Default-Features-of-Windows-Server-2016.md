---
layout: post
title: "Default Features of Windows Server 2016"
date: 2019-08-26 20:33:36 -0600
categories: [Windows]
---

Just for posterity, here are the default features of Windows Server 2016.

```
> Get-WindowsFeature | ? {$_.InstallState -eq "Installed"} | ft -autosize
 Display Name                          Name                      Install State
 ------------                          ----                      -------------
 [X] File and Storage Services         FileAndStorage-Services       Installed
     [X] Storage Services              Storage-Services              Installed
 [X] .NET Framework 4.6 Features       NET-Framework-45-Features     Installed
     [X] .NET Framework 4.6            NET-Framework-45-Core         Installed
     [X] WCF Services                  NET-WCF-Services45            Installed
         [X] TCP Port Sharing          NET-WCF-TCP-PortSharing45     Installed
 [X] SMB 1.0/CIFS File Sharing Support FS-SMB1                       Installed
 [X] Windows Defender Features         Windows-Defender-Features     Installed
     [X] Windows Defender              Windows-Defender              Installed
     [X] GUI for Windows Defender      Windows-Defender-Gui          Installed
 [X] Windows PowerShell                PowerShellRoot                Installed
     [X] Windows PowerShell 5.1        PowerShell                    Installed
     [X] Windows PowerShell ISE        PowerShell-ISE                Installed
 [X] WoW64 Support                     WoW64-Support                 Installed
 ```
 
