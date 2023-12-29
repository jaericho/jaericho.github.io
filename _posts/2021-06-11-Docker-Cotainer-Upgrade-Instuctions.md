---
layout: post
title: "Docker Container Upgrade Instructions"
date: 2021-06-11 08:00:00 -0600
categories: [Software]
tags: [Docker, Linux, NPM]
---

*I keep forgetting how to upgrade Docker containers because I use them so infrequently.*

Here are simple commands to upgrade the (very slick) [nginx-proxy-manager](https://nginxproxymanager.com/) container.

```bash
# Go into the directory with the .yaml file
cd ~/nginx-proxy-manager

# Stop the container
sudo docker-compose stop

# Pull the latest container
sudo docker-compose pull
# OR
# sudo docker pull jc21/nginx-proxy-manager

# Start the container again (-d for detached)
sudo docker-compose up -d
```

Looks like just doing `docker-compose pull` will stop the containers, so even the `docker-compose stop` might not be necessary.

Update: I found the [page](https://nginxproxymanager.com/upgrading/) that gives the same instructions.
