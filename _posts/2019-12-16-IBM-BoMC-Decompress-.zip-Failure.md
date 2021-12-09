---
layout: post
title: "IBM BoMC Decompress .zip Failure"
date: 2019-12-16 20:33:36 -0600
categories: [Stupid Bugs]
---
The IBM Bootable Media Creator BoMC v11.7 doesn’t like long file paths and you’ll receive an error about decompressing a zip file if the path is too long.

The workaround is to run it from a short filesystem path like `C:\temp\`

Get with the program IBM.
