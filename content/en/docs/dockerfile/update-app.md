---
title: "Update App"
description: ""
lead: "Update the application"
date: 2022-06-26T00:14:22+08:00
lastmod: 2022-06-26T00:14:22+08:00
draft: false
images: []
menu:
  docs:
    parent: ""
weight: 670
toc: true
---

As a small feature request, we’ve been asked by the product team to change the “empty text” when we don’t have any todo list items. They would like to change it to the following:
{{< alert icon="👉" text="You have no todo items yet! Add one above!" />}}

Pretty simple, right? Let’s make the change.

### Update the source code

  1. In the src/static/js/app.js file, update line 56 to use the new empty text.
  ```
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
  ```

  Let’s build our updated version of the image, using the same command we used before.

  ```
      docker build -t todoapp .
  ```

  Let’s start a new container using the updated code.

  ```
      docker run -dp 3000:3000 todoapp
  ```

  Uh oh! You probably have encountered an error !!!


### Replace the old container

To remove a container, it first needs to be stopped. Once it has stopped, it can be removed. We have two ways that we can remove the old container. Feel free to choose the path that you’re most comfortable with.

1. Remove a container using the CLI

  Get the ID of the container by using the docker ps command.
  
  ```
  docker ps
  ```

  Use the docker stop command to stop the container.

  Swap out <the-container-id> with the ID from docker ps

  ```
  docker stop <the-container-id>
  ```

  Once the container has stopped, you can remove it by using the docker rm command.

  ```
  docker rm <the-container-id>
  ```

2. Remove container from Docker Dashboard (if you removed the container through CLI you can't delete the same container again.)


### Start the updated app container

  1. Now, start your updated app.

  ```
  docker run -dp 3000:3000 getting-started
  ```

  2. Refresh your browser on http://localhost:3000 and you should see your updated help text!