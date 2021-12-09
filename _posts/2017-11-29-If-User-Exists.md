---
layout: post
title: "If User Exists?"
date: 2017-11-29 10:00:00 -0600
categories: [Powershell]
tags: [Active Directory, Windows]
---

Getting a simple script to check if an AD user exists has been a nightmare. I wanted something simple and straightforward and I finally found it.

{% highlight posh %}
$userobj = $(try {Get-ADUser $user} catch {$null})
if ($userobj -ne $null) {
   "$user exists"
}
else {
   "$user not found"
}
{% endhighlight %}

Another options would be to use dsquery:

{% highlight posh %}
if (dsquery user -samid $user) {
   "$($user.name) exists"
}
else {
   "$($user.name) not found"
}
{% endhighlight %}

These are the simplest options I can find.
