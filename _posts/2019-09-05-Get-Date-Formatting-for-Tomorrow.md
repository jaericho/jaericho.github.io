---
layout: post
title: "Get-Date Formatting for Tomorrow"
date: 2019-09-04 20:33:36 -0600
categories: [Powershell]
---

I had an almost identical question as [posted here](https://social.technet.microsoft.com/Forums/ie/en-US/b5dbe9fc-e716-44ca-8f18-36864bcae791/powershell-getdate-minus-one-day). I’m glad someone had the answer.

I was trying to get the tomorrow date in this exact format `mm/dd/yyyy`; however, Powershell kept returning `mm-dd-yyyy`; and if I used the Unix format of `-UFormat %m/%d/%Y`, then the result was a string and I couldn’t use `.AddDays(1)` on the Get-Date cmdlet.

Here was the solution:
{% highlight posh %}
Get-Date -Date $(Get-Date).AddDays(1) -UFormat "%m/%d/%Y"
{% endhighlight %}

This is running the Get-Date cmdlet to return a date (`-Date`)...
Which date? Today’s date +1 (`$(Get-Date).AddDays(1)`),
then format it the way I want: (`-UFormat "%m/%d/%Y"`)
