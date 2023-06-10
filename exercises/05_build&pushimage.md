# Build and Push an Image - Exercise
* Goal:
The goal of this exercise is to create an image based off of a Dockerfile you create. You will also
host this image on Docker Hub.

* Instructions:

* Create a Docker Hub Account

* Create an account on Docker Hub. This account will allow you to host your own images.
Visit https://hub.docker.com/signup in your favorite web browser.

* Follow the instructions on the screen by choosing a username (Docker ID) and a password. Be sure
to accept any items such as the privacy policy and terms of service.

* Create a Dockerfile

* Using Debian as the base image, install the nano editor package. Also, have bash start by default
when the container based off of your image is executed.

* First, create a temporary directory to work in.
mkdir tempbuild

* Change into the directory you created.
cd tempbuild

* Create a Dockerfile by opening it with a text editor such as nano. (NOTE: Use your favorite text
editor for the operating system you are working on. For example, nano is not installed by default on
Windows and some Linux distributions. For example, you can use notepad for Windows and
TexEdit for Mac.)

* Enter the following contents into the file. NOTE: It is very important that the contents are exact.
Capitalization, punctuation, and spacing matter!

```
FROM debian:stable
LABEL maintainer="ENTER_YOUR_NAME_HERE"
RUN apt update && apt install -y nano && apt clean
CMD [ "/bin/bash" ]
```

* Save the Dockerfile. If you are using nano, type Ctrl-o. Next hit "Enter" to save the file. Finally, type
Ctrl-x to exit the nano editor.

* Build the Image from the Dockerfile

* Build the image using your Docker Hub ID as the name space, "nanotest" as the repository, and
"latest" as the tag.

* For example, if your Docker ID is "robertsmith", then use "robertsmith/nanotest:latest".
docker build -t YOUR_DOCKER_ID/nanotest:latest .
NOTE: You could also use "YOUR_DOCKER_ID/nanotest". Remember that the "latest" tag is used if
no tag is specified.

* After the build completes, check that the image is available on your local Docker host:
docker images

* You should see the nanotest image is present.

* Start a Container Using the Image

* Test that your image starts bash and contains the nano package as expected.
docker run --name nanotest -it YOUR_DOCKER_ID/nanotest

* You should be presented with a bash prompt. Now, see if nano is available.
which nano

* If nano is available, the above command will report the path to the nano executable: "/bin/nano"
http://www.LinuxTrainingAcademy.com

* Exit out of the container.
```
exit
```

* Push the Image to Docker Hub

* Login to the Docker Hub registry using your Docker Hub ID.
```
docker login
```
* Provide your ID and password when prompted.
* Push your image to Docker Hub.
```
docker push YOUR_DOCKER_ID/nanotest:latest
```
