---
layout: post
title:  "Web Redirects"
date:   2020-09-10 08:00:00 -0600
categories: [Software]
tags: [Alpine Linux, darkhttpd, nginx, Redirects, WWW]
---

*[Alpine](https://www.alpinelinux.org) and [darkhttpd](https://unix4lyfe.org/darkhttpd/) work great, but [nginx](https://www.nginx.com/) might be a better fit.*

## Redirect Basics

I had to learn about redirecting webpages. The boss wanted the users to be able to type a simple word in the browser and be redirect to our new fancy cloud environment. For example, `http://cloud` would redirect users to the production environment, and `http://cloud-test/` would take them to the test environment. Simple enough. However, DNS alias might have added cert errors and I definitely wanted to avoid all that. And I had to make sure I did it right the first time. Since everything I make in QA is automatically published to production. Oy vey.

My first attempt was just serving up a simple webpage with a `meta` tag redirect.

```html
<meta http-equiv="refresh"
        content="3; URL=https://cloud.mycompany.cloudprovider.com" />
```

I worked, but the boss didn't like the three second timer. Ok, I set it to zero and all was good.

Then I found that I don't need a webpage at all. The webserver can do redirects.

Since I was serving up static webpages, my first attempt was built on Alpine Linux and darkhttpd. A small, lightweight linux distribution with a small, lightweight static http webserver.

I learned that darkhttpd doesn't have config files. It's config is set with the command line arguments that start it. But I could add `--forward cloud https://cloud.mycompany.cloudprovider.com` to the args in the openrc script: `/etc/init.d/darkhttpd`

Of course, I had to add the test environment: `--forward cloud-test https://cloud-test.mycompany.cloudprovider.com` and then I had to add the FQDN's too to make it all bulletproof for my users: `--forward cloud.mycompany.com https://cloud.mycompany.cloudprovider.com --forward cloud-test.mycompany.com https://cloud-test.mycompany.cloudprovider.com`

> *You have to cover all the bases for users.*
>   --Me

The command line args were a little long in the end, but it worked, and the webserver redirect feels faster than the webpage meta tag method. *(It must be faster as there is nothing for the browser to download and parse.)*

But there is always a catch.

## *"Put it in the cloud."*

The boss wants it in the cloud for outside users just in case HQ goes down. *(I would think we'd have bigger issues if that happens.)* Well, there goes my alpine/darkhttpd setup. Goodbye my VM with 1 vcpu, 256MB of memory, and 512MB disk. Hello [Ubuntu](http://ubuntu.com) with 1 vcpu and at at least 1GB of memory and gobs of disk. I know it's not really a lot but Alpine felt so svelte compared to Ubuntu.

Also is there isn't a nice Ubuntu package for darkhttpd, so it's back to [Apache2](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview) or nginx. Either would have been fine for my use case. The two reasons I chose nginx over apache was that I found an example for doing redirects with nginx first, and I like the configuration syntax better.

I created separate configs for each redirect *(cloud/cloud-test)* and this is my example:

```
server {
    listen 80;
    server_name cloud cloud.mycompany.com;
    rewrite ^/(.*)$ https://cloud.mycompany.cloudprovider.com redirect;
}
```

*I could have combined them all into a single config file but I like the separation. I think it's easier to conceptualize adding and removing redirects.*

I'm still not sure if I should use `redirect;` or `permanent;`
