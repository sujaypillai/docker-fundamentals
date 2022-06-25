---
title: "Difference between container and image"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 630
toc: true
---

- A Docker container image describes a container environment. 

- A Docker container is an instance of that environment, running on Docker Engine. 

You can run multiple containers from the same image, and all of them will contain the same software and configuration, as specified in the image.

### Docker images and layers

When you define a Docker image, you can use one or more layers, each of which includes system libraries, dependencies and files needed for the container environment. Image layers can be reused for different projects. 

To save time, most Docker images start from a parent image.

For example, here is the Dockerfile of the [Ubuntu image we used previously](https://github.com/tianon/docker-brew-ubuntu-core/blob/fbca80af7960ffcca085d509c20f53ced1697ade/jammy/Dockerfile)


On top of this parent image, you can add layers that include additional software or specific configurations.

When a container runs, Docker adds a readable/writable top layer over the static image layers. This top layer is used by the container to modify files during runtime, and can also be used to customize the container. This way, multiple containers created from the same image can have different data.

