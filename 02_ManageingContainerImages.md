# To Pull a docker image

docker pull: This command is used to download Docker images from a container registry to your local machine. 
It fetches the specified image or images and saves them in our local Docker image cache, 
making them available for use with docker run. 
The basic syntax of the docker pull command is:

docker pull nginx

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
f03b40093957: Pull complete 
eed12bbd6494: Pull complete 
fa7eb8c8eee8: Pull complete 
7ff3b2b12318: Pull complete 
0f67c7de5f2c: Pull complete 
831f51541d38: Pull complete 
Digest: sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
Mohammads-MacBook-Air:~ mohammadashadali$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              f9c14fe76d50        9 days ago          143MB
```

The docker pull command is typically used when we want to obtain a specific Docker image without creating or running any containers.

# Docker Tag

The docker tag command is used to create a new tag for an existing Docker image. 
This allows us to assign an additional name or version identifier to an image, 
making it easier to reference or distribute.

below is the basic syntax of the docker tag command

docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]

In this command, SOURCE_IMAGE refers to the name or ID of the existing Docker image we want to tag, 
and TARGET_IMAGE is the name or ID we want to assign to the new tag.

Here's an example of how to use the docker tag command:

docker tag my-image:latest my-image:1.0

In this example, the existing image my-image with the tag latest is being tagged 
as my-image with the tag 1.0. This creates a new version of the image with the updated tag.

Sample output:

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              f9c14fe76d50        9 days ago          143MB
Mohammads-MacBook-Air:~ mohammadashadali$ docker tag nginx:latest nginx:myblog_stable
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              f9c14fe76d50        9 days ago          143MB
nginx               myblog_stable       f9c14fe76d50        9 days ago          143MB
```

# Deleting a docker image

To delete Docker images, we can use the docker rmi command (short for "remove image"). Here's the basic syntax:

docker rmi [OPTIONS] IMAGE [IMAGE...]

Delete a single image:

docker rmi my-image

Delete multiple images:

docker rmi image1 image2 image3

We can also use the -f or --force option to force the removal of an image even if it is being used by a container. 
However, keep in mind that if you forcefully remove an image that is in use, 
the associated containers might stop functioning correctly. Use this option with caution.

Here's an example of using the --force option to delete an image:

docker rmi --force my-image

Remember to replace my-image with the actual name or ID of the image you want to delete.

Sample Output:

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
nginx               latest              f9c14fe76d50        9 days ago          143MB
Mohammads-MacBook-Air:~ mohammadashadali$ docker rmi nginx:latest
Untagged: nginx:latest
Untagged: nginx@sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305
Deleted: sha256:f9c14fe76d502861ba0939bc3189e642c02e257f06f4c0214b1f8ca329326cda
Deleted: sha256:419f8948c50c723f2a5ac74428af3d804b5d0079d6df8f7f827663cf10cbc366
Deleted: sha256:1030aac4f1a8096ed58d3d4a2df55dd1b1b27d919ad156d97ad1f68081d0051a
Deleted: sha256:7d90b49d96c3036539ef144ecc27c01de03902d8ea166a0f7b77d11d3779c4bd
Deleted: sha256:551acb210764654af31b6cd51adaa74edc9a202587c3395fe0e9f95a2e097f8b
Deleted: sha256:3c530958db4c75c6fb409f339367aaf9a1e163c84718c035d4b09bebc83f43e7
Deleted: sha256:8cbe4b54fa88d8fc0198ea0cc3a5432aea41573e6a0ee26eca8c79f9fbfa40e3
```
