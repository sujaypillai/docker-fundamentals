---
title: "What is a container image?"
description: "Regularly update the installed npm packages to keep your Doks website stable, usable, and secure."
lead: ""
date: 2020-11-12T13:26:54+01:00
lastmod: 2020-11-12T13:26:54+01:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 610
toc: true
---

A container image is a static file with executable code that can create a container on a computing system. A container image is immutable—meaning it cannot be changed, and can be deployed consistently in any environment.

Container images include everything a container needs to run—the container engine such as Docker or CoreOS, system libraries, utilities, configuration settings, and specific workloads that should run on the container. 

The image shares the operating system kernel of the host, so it does not need to include a full operating system.

A container image is composed of layers, added on to a parent image (also known as a base image). 

Layers make it possible to reuse components and configurations across images. Constructing layers in an optimal manner can help reduce container size and improve performance.


{{< details "How to check layers in a docker image?" >}}
```bash
$ docker image history ubuntu

IMAGE          CREATED       CREATED BY                                      SIZE      COMMENT
27941809078c   2 weeks ago   /bin/sh -c #(nop)  CMD ["bash"]                 0B        
<missing>      2 weeks ago   /bin/sh -c #(nop)  ADD file:11157b07dde10107f…   77.8MB    

```
{{< /details >}}
