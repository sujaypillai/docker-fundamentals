---
title: "Docker Image Architecture"
description: ""
lead: ""
date: 2020-11-12T15:22:20+01:00
lastmod: 2020-11-12T15:22:20+01:00
draft: false
images: []
menu: 
  docs:
    parent: "help"
weight: 620
toc: true
---

Docker is the world’s most popular container engine, so we will focus our discussion of container image architecture on Docker.

A Docker image is a collection of files, including binaries, source code and other dependencies, needed to deploy a container environment. In Docker, there are two ways to create an images:

  * **Create an image from an existing container** - you can run a container from an existing image, modify the container environment, and save the result as a  new image.

  * **Dockerfile** - Docker provides a simple, human-readable configuration file that specifies what a Docker image should contain.

{{< details "What images are available on Docker Host?" >}}
```bash
$ docker image ls

REPOSITORY                  TAG            IMAGE ID       CREATED         SIZE
alpine/git                  latest         620bef75a214   4 days ago      39.4MB
node                        alpine         515db77e67c7   8 days ago      174MB
ansible                     latest         d174f0236d75   12 days ago     1.36GB
ubuntu                      latest         27941809078c   2 weeks ago     77.8MB
```
{{< /details >}}
