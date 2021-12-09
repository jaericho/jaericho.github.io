---
layout: post
title: "Dell Command | Update 3.1"
date: 2020-03-20 10:00:00 -0600
categories: [Software]
tags: [Dell, Dell Command Update]
---

*For posterity, because I had a helluva of a time trying to find this online.*

Dell Command | Update v3.1
Usage:

    dcu-cli.exe /<command> [-<option1>=<value1>] [-<option2>=<value2>]...

Commands:
    /help - Displays usage information.

    /scan - Performs a system scan to determine the updates for the current system configuration.
    This command supports the following options: -catalogLocation, -updateSeverity, -updateType,
        -updateDeviceCategory, -report, -silent, -outputLog

    /applyUpdates - Applies all updates for the current system configuration.
    This command supports the following options: -catalogLocation, -updateSeverity, -updateType,
        -updateDeviceCategory, -reboot, -silent, -outputLog, -autoSuspendBitLocker, -encryptionKey,
        -encryptedPassword, -encryptedPasswordFile

    /driverInstall - Installs all base drivers for the current system configuration on a freshly installed
        operating system.
    This command supports the following options: -driverLibraryLocation, -reboot, -silent, -outputLog

    /configure - Allows configuration of Dell Command | Update based on settings provided in the supported
        options.
    This command supports the following options: -importSettings, -exportSettings, -lockSettings,
        -biosPassword, -advancedDriverRestore, -driverLibraryLocation, -catalogLocation, -downloadLocation,
        -updateSeverity, -updateType, -updateDeviceCategory, -userConsent, -customProxy, -proxyAuthentication,
        -proxyHost, -proxyPort, -proxyUsername, -proxyPassword, -silent, -outputLog, -scheduleAction,
        -scheduleWeekly, -scheduleMonthly, -scheduleManual, -scheduleAuto, -scheduledReboot, -restoreDefaults,
        -autoSuspendBitLocker

    /generateEncryptedPassword - Generates an encrypted BIOS password.
    This command supports the following options: -encryptionKey, -password, -outputPath

    /version - Displays the version.

The following options are available to use with the commands:

    -catalogLocation - Allows the user to set the repository/catalog file location. If used with
        /applyUpdates, only one path may be specified.
    Expected value(s): <file path(s)>
    Ex: > dcu-cli /configure -catalogLocation=C:\catalog.xml;C:\catalog2.xml
    Ex: > dcu-cli /applyUpdates -catalogLocation=C:\catalog.xml

    -driverLibraryLocation - Allows the user to set the system driver catalog location. If this option is
        not specified, the driver library shall be downloaded from Dell.com. NOTE: Requires functional
        networking components.
    Expected value(s): <file path>
    Ex: > dcu-cli /configure -driverLibraryLocation=C:\Temp\DriverLibrary.cab

    -advancedDriverRestore - Allows the user to enable or disable the Advanced Driver Restore feature in the
        UI.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -advancedDriverRestore=disable

    -updateSeverity - Allows the user to filter updates based on severity.
    Expected value(s): (critical,recommended,optional)
    Ex: > dcu-cli /configure -updateSeverity=recommended,optional

    -updateType - Allows the user to filter updates based on update type.
    Expected value(s): (bios,firmware,driver,application,others)
    Ex: > dcu-cli /configure -updateType=bios

    -updateDeviceCategory - Allows the user to filter updates based on device type.
    Expected value(s): (audio,video,network,storage,input,chipset,others)
    Ex: > dcu-cli /configure -updateDeviceCategory=network,storage

    -importSettings - Allows the user to import application settings file. NOTE: This option cannot be used
        with any other options except -outputLog and -silent.
    Expected value(s): <file path>
    Ex: > dcu-cli /configure -importSettings=C:\Temp\Settings.xml

    -lockSettings - Allows the user to lock all the settings in the UI. NOTE: This option cannot be used
        with any other options except -outputLog and -silent.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -lockSettings=enable

    -exportSettings - Allows the user to export application settings to the specified folder path. NOTE:
        This option cannot be used with any other options except -outputLog and -silent.
    Expected value(s): <folder path>
    Ex: > dcu-cli /configure -exportSettings=C:\Temp\

    -reboot - Reboot the system automatically (if required).
    Expected value(s): <enable|disable>
    Ex:> dcu-cli /applyUpdates -reboot=enable

    -userConsent - Allows the user to opt-in or opt-out to send information to Dell regarding the update
        experience.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -userConsent=disable

    -report - Allows the user to create an XML report of the applicable updates.
    Expected value(s): <folder path>
    Ex: > dcu-cli /scan -report=C:\Temp\

    -biosPassword - Allows the user to provide the unencrypted BIOS password. The password will be cleared
        if a password is not provided or "" is supplied. NOTE: The value needs to be enclosed in double quotes.
    Expected value(s): <password|"">
    Ex: > dcu-cli /configure -biosPassword="Test1234"

    -downloadLocation - Allows the user to specify the location to override the default application download
        path.
    Expected value(s): <folder path>
    Ex: > dcu-cli /configure -downloadLocation=C:\Temp\AppDownload

    -silent - Allows the user to hide status and progress information on the console.
    Expected value(s): None
    Ex: > dcu-cli /scan -silent

    -outputLog - Allows the user to log the status and progress information of a command execution in a
        given log path.
    Expected value(s): <file path> with .log extension
    Ex: > dcu-cli /scan -outputLog=C:\Temp\scanOutput.log

    -customProxy - Allows the user to enable or disable the use of custom proxy. NOTE: Setting this option
        to enable will cause validation of all custom proxy settings.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -customProxy=enable

    -proxyHost - Allows the user to specify the proxy host. Giving an empty string as the value to this
        option clears proxy host. NOTE: Changing this option will cause validation of all custom proxy settings.
    Expected value(s): <FQDN|IP address|"">
    Ex: > dcu-cli /configure -proxyHost=proxy.com
    Ex: > dcu-cli /configure -proxyHost=""

    -proxyPort - Allows the user to specify the proxy port. Giving an empty string as the value to this
        option clears proxy port. NOTE: Changing this option will cause validation of all custom proxy settings.
    Expected value(s): <port|"">
    Ex: > dcu-cli /configure -proxyPort=8080
    Ex: > dcu-cli /configure -proxyPort=""

    -proxyAuthentication - Allows the user to enable or disable the use of proxy authentication. NOTE:
        Changing this option will cause validation of all custom proxy settings.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -proxyAuthentication=enable

    -proxyUsername - Allows the user to specify the proxy username. Giving an empty string as the value to
        this option clears proxy username. NOTE: Changing this option will cause validation of all custom proxy
        settings.
    Expected value(s): <username|"">
    Ex: > dcu-cli /configure -proxyUsername="john doe"
    Ex: > dcu-cli /configure -proxyUsername=""

    -proxyPassword - Allows the user to specify the proxy password. Giving an empty string as the value to
        this option clears proxy password. NOTE: Changing this option will cause validation of all custom proxy
        settings. The value needs to be enclosed in double quotes
    Expected value(s): <password|"">
    Ex: > dcu-cli /configure -proxyPassword="my password"
    Ex: > dcu-cli /configure -proxyPassword=""

    -scheduleAction - Allows the user to specify the action to perform when updates are found.
    Expected value(s): <NotifyAvailableUpdates | DownloadAndNotify | DownloadInstallAndNotify>
    Ex: > dcu-cli /configure -scheduleAction=NotifyAvailableUpdates

    -scheduleWeekly - Allows the user to specify the day of the week and time on which to schedule an
        update. NOTE: This option cannot be used with -scheduleManual, -scheduleAuto, -scheduleMonthly.
    Expected value(s): Day [< Sun | Mon | Tue | Wed | Thu | Fri | Sat >],Time[00:00(24 hr format, 15 mins
        increment)]
    Ex: > dcu-cli /configure -scheduleWeekly=Mon,23:45

    -scheduleMonthly - Allows the user to specify the day of the month and time on which to schedule an
        update. If the scheduled day is greater than the last day of the month, the update will be performed on
        the last day of that month. NOTE: This option cannot be used with -scheduleManual, -scheduleAuto,
        -scheduleWeekly
    Expected value(s): Date of month [1 - 31],Time[00:00(24 hr format, 15 mins increment)]
    Ex: > dcu-cli /configure -scheduleMonthly=28,00:45

    -scheduleManual - Allows the user to disable the automatic schedule and enable only manual updates.
        NOTE: This option cannot be used with -scheduleAuto, -scheduleWeekly, -scheduleMonthly
    Expected value(s): None
    Ex: > dcu-cli /configure -scheduleManual

    -scheduleAuto - Allows the user to enable the default automatic update schedule. NOTE: Automatic updates
        execute every 3 days. Also, this option cannot be used with -scheduleManual, -scheduleWeekly,
        -scheduleMonthly
    Expected value(s): None
    Ex: > dcu-cli /configure -scheduleAuto

    -scheduledReboot - Allows the user to schedule a reboot time, in minutes, after updates are applied.
    Expected value(s): <0|5|15|60> (NOTE: 0=Never reboot)
    Ex: > dcu-cli /configure -scheduledReboot=5

    -encryptedPassword - Allows the user to pass the encrypted password in-line along with the encryption
        key that was used to generate it. NOTE: -encryptionKey is required to be specified along with this
        option. Also, this value needs to be enclosed in double quotes.
    Expected value(s): <encrypted password>
    Ex: > dcu-cli /applyUpdates -encryptedPassword="myEncryptedPassword" -encryptionKey="myEncryptionKey"

    -encryptionKey - Allows the user to specify the encryption key used to encrypt the password. NOTE: The
        key provided must be at least six nonwhitespace characters and include an uppercase letter, a lowercase
        letter, and a digit. Also, this value needs to be enclosed in double quotes.
    Expected value(s): <encryption key>
    Ex: > dcu-cli /applyUpdates -encryptedPassword="myEncryptedPassword" -encryptionKey="myEncryptionKey"
    Ex: > dcu-cli /generateEncryptedPassword -encryptionKey="myEncryptionKey" -password="myPassword"
        -outputPath=C:\Temp

    -encryptedPasswordFile - Allows the user to pass the encrypted password via file. NOTE: -encryptionKey
        is required to be specified along with this option.
    Expected value(s): <file path>
    Ex: > dcu-cli /applyUpdates -encryptedPasswordFile=C:\Temp\EncryptedPasswordFile.txt
        -encryptionKey="myEncryptionKey"

    -password - Allows the user to specify the password to be encrypted. NOTE: -encryptionKey is required to
        be specified along with this option. Also, this value needs to be enclosed in double quotes.
    Expected value(s): <password>
    Ex: > dcu-cli /generateEncryptedPassword -encryptionKey="myEncryptionKey" -password="myPassword"

    -outputPath - Allows the user to specify the folder path to which encrypted password file is saved.
    Expected value(s): <folder path>
    Ex: > dcu-cli /generateEncryptedPassword -encryptionKey="myEncryptionKey" -password="myPassword"
        -outputPath=C:\Temp

    -restoreDefaults - Allows the user to restore default settings.
    Expected value(s): None
    Ex: > dcu-cli /configure -restoreDefaults

    -autoSuspendBitLocker - Allows the user to enable or disable the automatic suspension of BitLocker, when
        applying BIOS updates.
    Expected value(s): <enable|disable>
    Ex: > dcu-cli /configure -autoSuspendBitLocker=enable
