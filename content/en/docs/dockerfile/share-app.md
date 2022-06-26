---
title: "Share the application"
description: ""
lead: "Now that we’ve built an image, let’s share it!"
date: 2022-06-26T08:26:09+08:00
lastmod: 2022-06-26T08:26:09+08:00
draft: false
images: []
menu:
  docs:
    parent: ""
weight: 680
toc: true
---

To share Docker images, you have to use a Docker registry. The default registry is Docker Hub and is where all of the images we’ve used have come from.

### Push the image
  1. In the command line execute the below push command:
  
  ```
    docker push todoapp
  ```

  Why did it fail?
  ```
    docker push todoapp
    The push refers to repository [docker.io/library/todoapp]
    7962b4fa86f9: Layer already exists 
    70fff1b8b419: Layer already exists 
    67bb22608009: Layer already exists 
    24302eb7d908: Layer already exists 
    errors:
    denied: requested access to the resource is denied
    unauthorized: authentication required
  ```

  The push command was trying to upload an image named `docker.io/library/todoapp`, which is repository for official docker images owened by Docker.

  To fix this, we need to “tag” our existing image we’ve built to give it another name.

  2. Login to the Docker Hub using the command docker login -u YOUR-USER-NAME.

  3. Use the `docker tag` command to give the `todoapp` image a new name. Be sure to swap out YOUR-USER-NAME with your Docker ID.

      ```
        docker tag todoapp YOUR-USER-NAME/todoapp
      ```
  4. Now try your push command again. If you don’t specify a tag, Docker will use a tag called latest

      ```
        docker push YOUR-USER-NAME/todoapp
      ```

### Run the image on a new instance

Now that our image has been built and pushed into a registry, let’s try running our app on a brand new instance that has never seen this container image! 

Try exchanging the image you created by pulling your colleagues docker image.


***You may try this on [Play with Docker](https://labs.play-with-docker.com/)***