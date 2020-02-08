---
layout: post
title:  "Reverse Proxy with Certs"
date:   2018-07-10 20:33:36 -0600
categories: [linux]
tags: [Reverse Proxy, Certs, webserver]
---

[Here](https://tylermade.net/2017/09/14/the-perfect-reverse-proxy-nginx-ssl-webui-management) is a great tutorial for setting up a reverse proxy for webservers.

Kudos to Tyler and the [Ajenti](http://ajenti.org/) project.

Caveats:
* As of 2018-07-10, Ajenti didn’t work on Ubuntu 18.04, a dependency was broken.
* I setup the cert for site1.domain.com, then site2.domain.com complained it was using site1’s cert, until I ran certbot and gave site2 it’s own cert. Then everything was working.

UPDATE: I've heard that the Ajenti project is dead. Perhaps I'll try Traefik in the future. It looks to be the new hotness for reverse proxies and more.