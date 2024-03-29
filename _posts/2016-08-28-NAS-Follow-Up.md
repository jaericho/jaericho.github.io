---
layout: post
title: "NAS (Follow Up)"
date: 2016-08-28 10:00:00 -0600
categories: [Hardware]
tags: [Build, FreeNAS, NAS, Storage]
---

Last Febuary I built a [NAS]({% post_url 2016-02-02-NAS %}) and I learned two things:

1. Overbuild.
1. Get a good case.

## Overbuild

When I chose the [Supermicro A1SRi-2558F](http://www.supermicro.com/products/motherboard/Atom/X10/A1SRi-2558F.cfm), I wanted it because it was a robust board, low wattage, and an all Intel SATA chipset. It only has 6 SATA ports but I figured that would be plenty. Also the runner-up was a commonly used ASRock motherboard with 12 SATA ports but some of those SATA ports used a Marvell controller and at the time there were several forum posts about Marvell controllers losing the drives that were attached. So I figured I’d go the safe route and chose all Intel.

Six-months later, iX Systems announced their new [FreeNAS Mini appliance](https://www.ixsystems.com/freenas-mini/) and it looks like it uses that same ASRock motherboard. Maybe the bugs were worked out?

# Hindsight

It’s too early to tell, but in a year or so I may be kicking myself for limiting the SATA ports. If I want to expand storage I’ll need to buy a SATA pci-e card and that will burn up the only slot the A1SRi has, and I’d like to do 10G networking too.

## Get a Good Case

Initially, I reused an old case I had lying around. It was a Lian-Li PC60 and it has served me well over the past 10+ years. However the airflow wasn’t as good as some of the more modern products and the fans were just tiny. At a friends recommendation I purchased a [Fractal Design – Define R5](http://www.fractal-design.com/home/product/cases/define-series/define-r5-black) and it’s the best case I have ever seen. This case is amazing, and it will definitely be worth every penny. Especially if I ever have to replace a drive.

# Hindsight

Don’t reuse a case that’s 10+ years old. The modern cases have much better designed cable management, expansion, and airflow.

Over all I think I did fairly well for my first NAS. Up next is to rebuild my ESXi server that’s running [Plex](https://plex.tv) and [owncloud](http://owncloud.org/). I also have a [computer rack](https://www.amazon.com/Alera-Complete-Shelving-Caster-Anthracite/dp/B005SG1FE6) all setup for it now.

![pic](/assets/2016/08/img_0127.jpg)

![pic](/assets/2016/08/img_0125.jpg)
