---
title: "Sample App"
description: ""
lead: ""
date: 2022-06-25T17:59:53+08:00
lastmod: 2022-06-25T17:59:53+08:00
draft: false
images: []
menu:
  docs:
    parent: ""
weight: 660
toc: true
---

Lets start building a sample app to understand more about `Dockerfile`.

The sample app is a simple todo list manager running in NodeJS. Source code is ready so don't need to worry if you don't know NodeJS :)


### Get the app

  1. [Download the app contents](https://github.com/docker/getting-started/tree/master/app)

  2. Once downloaded open the project in VSCode

  3. You should see the `package.json` and two subdirectories (`src` & `spec`)


### Build the app’s container image

  1. Create a file named Dockerfile in the same folder as the file package.json with the following contents.

  ```bash
    # syntax=docker/dockerfile:1
    FROM node:12-alpine
    RUN apk add --no-cache python2 g++ make
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "src/index.js"]
    EXPOSE 3000
  ```

  2. Open a terminal and go to the app directory with the `Dockerfile`. Now build the container image using the `docker build` command.

  ```bash
    docker build -t todoapp .
  ```
  This command used the Dockerfile to build a new container image. You might have noticed that a lot of “layers” were downloaded. This is because we instructed the builder that we wanted to start from the node:12-alpine image. But, since we didn’t have that on our machine, that image needed to be downloaded.

  After the image was downloaded, we copied in our application and used yarn to install our application’s dependencies. The CMD directive specifies the default command to run when starting a container from this image.

  Finally, the -t flag tags our image. Think of this simply as a human-readable name for the final image. Since we named the image getting-started, we can refer to that image when we run a container.

  The . at the end of the docker build command tells Docker that it should look for the Dockerfile in the current directory.


### Start an app container

Now that we have an image, let’s run the application. To do so, we will use the docker run command 

  1. Start your container using the docker run command and specify the name of the image we just created:
  ```bash
  docker run -dp 3000:3000 getting-started
  ```

  2. After a few seconds, open your web browser to http://localhost:3000. You should see our app.

  3. Go ahead and add an item or two and see that it works as you expect. You can mark items as complete and remove items. Your frontend is successfully storing items in the backend. Pretty quick and easy, huh?

At this point, you should have a running todo list manager with a few items, all built by you. Now, let’s make a few changes and learn about managing our containers.

If you take a quick look at the Docker Dashboard, you should see your two containers running now (this tutorial and your freshly launched app container).