---
title: "Base and  Parent Image"
description: ""
lead: ""
date: 2020-11-12T13:26:54+01:00
lastmod: 2020-11-12T13:26:54+01:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 640
toc: true
---

There is a subtle technical difference between base and parent images:

  - **A base image** is an empty container image, which allows advanced users to create an image from scratch.
  - **A parent image** is a pre-configured image that provides some basic functionality, such as a stripped-down Linux system, a database such as MySQL or PostgreSQL, or a content management system such as WordPress. 

However, in the container community, the terms “base image” and “parent image” are often used interchangeably.

There is a large number of ready-made parent images available on Docker Hub, and on many other public container repositories. You can also use your own images as a parent for new images.

### Docker Manifest

 - Each Docker image comes with a file called a ***manifest***. 

 - This is a JSON file that describes the image and provides metadata such as tags, a digital signature to verify the origin of the image, and documentation.

### Container Repository

Docker Hub is the world’s largest container image registry. You can use it to access publicly available Docker images, or store your own images. There are many other tools you can use to manage a container image repository, including:

 * Azure Container Registry (ACR)
 * Amazon Elastic Container Registry (ECR)
 * Google Container Registry
 * Harbor
 * JFrog Artifactory
 * Red Hat Quay
