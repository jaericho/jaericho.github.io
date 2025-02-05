# CyberArk Needs Work

## EPM

* When pasting a definition, add it to the top of the list just like when a new definition is added.
* Can't move definitions to another policy easily. Copy/Paste one at a time doesn't cut it.
* Can't wildcard search names of computers. (i.e. "2*")
* EPM dashboard is stuck on DST.
* At least they added the checkbox to the parameters screen.

## PAM

* Editing a device should lose your place in the Accounts View. How many times do I have to retype my search criteria?
* Cisco Router via SSH doesn't support [Secret](https://cyberark-customers.force.com/s/article/00002207) out of the box. And CyberArk support doesn't seem to know anything about it.
* MSSQLManagementStudioDatabaseAuthenticationDispatcher.exe is not added to AppLocker by default, but MSSQLManagementStudioWindowsAuthenticationDispatcher.exe is.
* MSSQL setup instructions don't mention that the ODBC driver is necessary.
* PAM needs a much easier way to update the Notes field.
* Needs a way to mass edit Safe members and their permissions.
* PGU needs to support special characters in passwords. (but this might be a selenium issue. I don't know.)

They do finally have their own client so using RDCMan isn't required. It's ugly as sin but it does support SAML, and you only need to login once which is a big win.

# Cert upgrades in windows

How to do cert upgrades in [Windows](https://dirteam.com/sander/2022/09/14/todo-upgrade-the-certificates-for-your-windows-server-2016-based-domain-controllers-and-up-to-enable-windows-hello-for-business-hybrid-scenarios/)

# Inconsistent Powershell

Get-networkfirewallprofile isn't [accurate](https://stackoverflow.com/questions/31058090/windows-firewall-state-different-between-powershell-output-and-gui)

# Handbrake, Subtitle-Default, and JSON

You can use SubtitleDefault with Handbrake's .json config files.
