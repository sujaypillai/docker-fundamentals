---
title: "What Is Dockerfile"
description: ""
lead: ""
date: 2022-06-25T12:39:13+08:00
lastmod: 2022-06-25T12:39:13+08:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 650
toc: true
---

- A **Dockerfile** is is a simple text file with instructions on how to build your images.

- Using `docker build` users can create an automated build that executes several command-line instructions in succession.

## Usage

The `docker build` command builds an image from a Dockerfile and a context. 

The build’s context is the set of files at a specified location `PATH` or `URL`. 

  * The `PATH` is a directory on your local filesystem. 

  * The `URL` is a Git repository location.


The build is run by the Docker daemon, not by the CLI.

The first thing a build process does is send the entire context (recursively) to the daemon. 

In most cases, it’s best to start with an empty directory as context and keep your Dockerfile in that directory. Add only the files needed for building the Dockerfile.

To use a file in the build context, the Dockerfile refers to the file specified in an instruction, for example, a COPY instruction. 

To increase the build’s performance, exclude files and directories by adding a `.dockerignore` file to the context directory. 

Traditionally, the Dockerfile is called `Dockerfile` and located in the root of the context. You use the -f flag with docker build to point to a Dockerfile anywhere in your file system.

```bash
 docker build -f /path/to/a/Dockerfile .
```

You can specify a repository and tag at which to save the new image if the build succeeds:

```bash
 docker build -t sujaypillai/testapp .
```

Before the Docker daemon runs the instructions in the Dockerfile, it performs a preliminary validation of the Dockerfile and returns an error if the syntax is incorrect:

```bash
 docker build -t test/myapp .

[+] Building 0.3s (2/2) FINISHED
 => [internal] load build definition from Dockerfile                       0.1s
 => => transferring dockerfile: 60B                                        0.0s
 => [internal] load .dockerignore                                          0.1s
 => => transferring context: 2B                                            0.0s
error: failed to solve: rpc error: code = Unknown desc = failed to solve with frontend dockerfile.v0: failed to create LLB definition:
dockerfile parse error line 2: unknown instruction: RUNCMD
```
The Docker daemon runs the instructions in the Dockerfile one-by-one, committing the result of each instruction to a new image if necessary, before finally outputting the ID of your new image. The Docker daemon will automatically clean up the context you sent.

Whenever possible, Docker uses a build-cache to accelerate the docker build process significantly. This is indicated by the CACHED message in the console output.

## Format

Here is the format of the Dockerfile:

```bash
# Comment
INSTRUCTION arguments
```

The instruction is not case-sensitive. However, convention is for them to be UPPERCASE to distinguish them from arguments more easily.

Docker runs instructions in a Dockerfile in order. A Dockerfile must begin with a FROM instruction.

This may be after parser directives, comments, and globally scoped ARGs. 

The FROM instruction specifies the Parent Image from which you are building. 

FROM may only be preceded by one or more ARG instructions, which declare arguments that are used in FROM lines in the Dockerfile.