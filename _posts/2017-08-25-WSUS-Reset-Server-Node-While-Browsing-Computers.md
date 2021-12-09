---
layout: post
title: "WSUS: Reset Server Node While Browsing Computers"
date: 2017-08-25 10:00:00 -0600
categories: [Stupid Bugs]
tags: [BIOS, Windows, WSUS]
---

I’ve run into another very annoying WSUS bug and this one deals with Computer Model information being corrupted when being entered into the SUS DB.

![wsus_groups.png](/assets/2017/08/wsus_groups.png)

Crashing groups highlighted in red.

Twice I’ve encountered a bug where the WSUS console would crash every time I tried to browse the All Computers or Unassigned Computers groups, but it wouldn’t crash when I browse another sub-group.

I found a very useful blog post that showed how to fix it but I’m unable to find it now; however, I was able to remember the steps I took.

# New Method

UPDATE 2020-02-08: I found an easier method of doing this. It still occurs a couple times a year.

1. Find the entry with the bad data. For me it's usually the ComputerModel field.
    ```sql
    SELECT * FROM tbComputerTargetDetail
    WHERE ComputerModel
    NOT LIKE '[a-z]%'
    ```
1. Update the bad data to anything else. (I normally choose 'blank')
    ```sql
    UPDATE tbComputerTargetDetail
    SET ComputerModel = ''
    WHERE TargetID = '<targetid>'
    ```

# Old Method

1. Using SSMS, export the table `tbComputerTargetDetail` to a csv. (Select * query, then save the results as csv.)
1. Sort the various columns to find the one with the box (like an unknown character). This is the corrupt entry. For me, it's always been the ComputerModel field.
![wsus_corrupt_example.png](/assets/2017/08/wsus_corrupt_example.png "A similar example.")
1. Note the TargetID #.
1. You can use the TargetID number in the tbComputerTarget table to find out the hostname of the offending machine for a permanent fix.
    ```sql
    SELECT FullDomainName
    FROM [SUSDB].[dbo].[tbComputerTarget]
    WHERE TargetID = '<targetid#>'
    ```
1. Blank out the field with the bad data.
    ```sql
    UPDATE [SUSDB].[dbo].[tbComputerTargetDetail]
    SET ComputerModel=''
    FROM [SUSDB].[dbo].[tbComputerTargetDetail]
    WHERE TargetID='<targetid#>'
    ```

WSUS will be working again.

For a more permament fix, I've only needed to update the BIOS on the workstation.
