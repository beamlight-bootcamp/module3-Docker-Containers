# Managing Images Exercise
* Goal:
The goal of this exercise is to familiarize you with downloading and deleting images. 
In this exercise, you'll focus on two popular applications, Jenkins and Apache.

* Instructions:

* Download The Images:
In order to download, or “pull”, the “jenkins” container image, use the following command: 

```
docker pull jenkins/jenkins:lts
```

(NOTE: the ":latest" tag is optional because if no tag is supplied the "latest" tag is assumed.)

Next, download the “Apache” image. This image is actually called “httpd.”
You can determine the name of the image by searching for on the command line with "docker search TERM" 
or by searching on https://hub.docker.com.

Download the "2-alpine" version of this image instead of the default “latest” image:
```
docker pull httpd:2-alpine
```

This image contains Apache version 2, running on the Alpine Linux distribution as its base.
Because of its small size, Alpine is heavily used in containers.
If that tag becomes outdated and doesn’t work for you then visit this page on Docker Hub to get a working tag:
https://hub.docker.com/_/httpd?tab=tags
Check the images are present
Let’s list the two images that we downloaded:

```
docker images
```

Check to see how much disk space all of images combined are using.

```
docker system df
```

Delete the Images
Now delete each of the two images. To delete Jenkins use this command:

```
docker rmi jenkins/jenkins
```

Note there’s no tag because we have the “latest” tag of Jenkins.
For Apache we have to declare the tag explicitly or the “rmi” command won’t work.

```

docker rmi httpd:2-alpine
```

Check That the Images Are Deleted
Make sure the images aren’t present with this command:

```
docker images
```
