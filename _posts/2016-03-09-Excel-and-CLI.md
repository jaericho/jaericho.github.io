---
layout: post
title: "Excel and CLI"
date: 2016-03-09 20:33:36 -0600
categories: [Software]
tags: [CLI, Excel, Powershell]
---

*Inspired from this post at [LoneSysAdmin.net](https://lonesysadmin.net/2016/03/03/use-microsoft-excel-for-your-text-manipulation-needs/)*

I found a neat little trick with excel. It’s old news but I found it useful.

I needed to run a couple commands across a bunch of servers and I had a list of the hostnames. I could have used Powershell to iterate over the list and run the commands but I was in a rush and needed something quick and dirty, so I used Excel.

Put the list of servers in Excel then concatenate (“&”) the rest of the commands in another cell. Then autofill the commands down.

![pic](/assets/2016/03/excel_trick2.png)

Maybe I should have forced myself to do Powershell and brush up on my skills but sometimes just getting something done without any hassle is needed.
