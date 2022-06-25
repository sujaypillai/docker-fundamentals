---
title: "Docker Desktop"
description: ""
lead: ""
date: 2022-06-24T21:59:39+08:00
lastmod: 2022-06-24T21:59:39+08:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 104
toc: true
---


### Run your first container

```
 docker run -i -t ubuntu /bin/bash
 ```


## What is a container?

Now that you've run a container, what _is_ a container? Simply put, a container is simply another process on your machine that has been isolated from all other processes on the host machine. That isolation leverages [kernel namespaces and cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), features that have been in Linux for a long time. Docker has worked to make these capabilities approachable and easy to use.

## What is a container image?

When running a container, it uses an isolated filesystem. This custom filesystem is provided 
by a **container image**. Since the image contains the container's filesystem, it must contain everything 
needed to run an application - all dependencies, configuration, scripts, binaries, etc. The 
image also contains other configuration for the container, such as environment variables,
a default command to run, and other metadata.

We'll dive deeper into images later on, covering topics such as layering, best practices, and more.