---
layout: post
title:  "Fast Blogs"
date:   2020-02-08 10:00:00 -0600
categories: [Meta]
tags: [Jekyll, Static Site Generator, Wordpress]
---

I use this blog to jot down things I want to remember or snippets I hope will help someone else.

# Too Slow

I noticed one day that my blog was a little sluggish. It was running on Wordpress's free ad-supported service. It's a nice service, and I have no beef with it, usually. The free themes are nice and you get much more than you pay for, so I really couldn't complain.

But the sluggishness was bugging me. In the age of gigabit speed internet connections why is there so much stuttering during load? Especially when this blog is mostly text and _maybe_ a picture every other post.

Most web browsers have a built in developer mode and Chrome's is especially nice since it can benchmark every element in the webpage and tell you what it took to download each one. I fired it up on my latest blog post and found that a full reload (skipping the cache) of one of my blogposts would download 6MB! That is *beyond* insane.

Well, it turns out that is a little misleading. The 6MB page download was true, but it only does that when I'm logged into Wordpress and had a Gravatar account linked to it. Regular visitors won't see that much. They'll see a 2.9MB webpage. Which is still _much_ too high for a blog consisting of 95% text.

With Wordpress the [Ivanti Issues]({% post_url 2020-01-30-Ivanti-Issues-2019-Edition %}) post would transfer 1.5MB of data, 2.9MB of resources, with over 70 requests in 500-900ms. And most of the requests are fetching ads, gravatar crap, fonts, and pictures that aren't even used in the post at all.

I only noticed this because I stumbled across another blog that loaded insanely fast: [x86.lol](https://x86.lol). I think it was running on Jekyll because it used the default Jekyll theme. And that pushed me into static site generators.

# Pre-compiled Websites

I know enough about web servers that they'll cache common requests in memory. They'll "compile" websites like source-code is compiled into a binary file, so when I found Static Site Generators will do the same thing with markdown and text files, I was intrigued. I like going fast and I want this blog to be as fast as possible while still looking good. SS64.com (one of my favorite sites, I use it almost daily) is an example of a website that strives for this.

> The website is designed with performance as a priority; the aim is to return relevant pages as fast as a local help index.
> 
> --[About SS64.com](https://ss64.com/docs/)

I want the same thing and downloading un-optimized 100KB jpg avatars of followers that aren't on the page I'm looking at is definitely not the same thing and not my style.

And maybe it has something to do with the fact that I use vscode everyday and now that I have a hammer, everything is a nail. But using github, vscode, and markdown as my workflow really appeals to me.

So I have tried a lot of SSG's trying to find one that was what I wanted and easy enough for me. I work in Windows all day and a lot of these open source programs are a pain in the ass to get going. npm, gem, ruby, bundle...ugh, I want to write in markdown, and serve it as plain html. No, .js, php, cgi, or databases. (The only db I like dealing with is sqlite because it's easy to backup. Wut? I'm a sysadmin by trade I hate dealing with db's.)

# Jekyll vs. Hugo

[Grav](https://getgrav.org/) was nice, but I wanted to just serve up static files and not run a webserver to create posts.

There were some documentation generators that looked sexy, but they weren't blog focused and not what I wanted.

It came down to [Jekyll](https://jekyllrb.com/) and [Hugo](https://gohugo.io/).

Hugo had an easier startup. I had it working on the first try. It has nice a few themes I really liked, but the YAML/TOML/JSON was a little confusing. And I couldn't figure out how to write markdown files outside of Hugo and have them work. I had to first create each new post with `hugo new post` then go back and edit the file in vscode. I didn't figure out what `hugo new post\my-new-post.md` did in the background other than create a new file.

Jekyll had a rougher start the first time I tried it. I tried it first because it was the most popular, failed, then tried Hugo. But after Hugo didn't pan out (I do like it, it's _almost_ there), I switched back to Jekyll and GitHub Pages. I figure this blog using GitHub Pages will be a good way to cut my teeth on Git and hell, it's a built-in backup.) I have to use a public repo to use the free GitHub Pages service, which I didn't like at first, but then I realized, it's a blog...the source code is the final product.

# Benchmarks

So how does the new Jekyll/Github Pages powered post look like in terms of benchmarks?

| | Transfer | Resources | Requests | Time
| WordPress | 1,500 K | 2,900 K | 70+ | 500-900ms
| Static | 8 K | 23 K | 3 | 130ms
| | down 99.5% | down 99.2% | down 95.7% | 5x to 9x faster

I like those results.
