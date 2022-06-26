---
title: "Dive into the volume"
description: ""
lead: ""
date: 2022-06-26T22:49:02+08:00
lastmod: 2022-06-26T22:49:02+08:00
draft: false
images: []
menu:
  docs:
    parent: ""
weight: 710
toc: true
---

A lot of people frequently ask “Where is Docker actually storing my data when I use a named volume?” 

If you want to know, you can use the `docker volume inspect` command.

```
$ docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

The `Mountpoint` is the actual location on the disk where the data is stored. Note that on most machines, you will
need to have root access to access this directory from the host. But, that's where it is!

>**Accessing volume data directly on Docker Desktop**
>
>While running in Docker Desktop, the Docker commands are actually running inside a small VM on your machine.
>If you wanted to look at the actual contents of the Mountpoint directory, you would need to first get inside
>of the VM.