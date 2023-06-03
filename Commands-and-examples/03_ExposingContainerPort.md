# Making containers publicly Available

In this lesson we wil learn how we can make our containers publicly available

If we want to examine run command of a particular image we could always find details
regarding that in the dockerhub. Let's say we want to see which port we can run nginx
container on, we can see this information by going to the following link

https://hub.docker.com/_/nginx

The format is usually https://hub.docker.com/_/ followed by the image name

Let's say we want to see similar information for jenkins container we can find that info by
going to

https://hub.docker.com/_/jenkins

Recommendation is to always use the docker official image

# Running a container by exposing the port

Example:

```
docker run --name our_nginx -d -p 8080:80 nginx
```

In this example, any traffic that arrives at port 8080 on the host machine will be forwarded to port 80 
within the Docker container.

It's important to note that the host-port can be any available port on the host machine. 
We can choose a port that is not already in use to avoid conflicts. On the other hand, 
the container-port should match the port that our application inside the Docker container is listening on. 
For example, if your application runs a web server on port 80 inside the container, we would typically map 
it to port 80 on the host machine.

Sample output of the above command

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker run --name our_nginx -d -p 8080:80 nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
f03b40093957: Pull complete 
eed12bbd6494: Pull complete 
fa7eb8c8eee8: Pull complete 
7ff3b2b12318: Pull complete 
0f67c7de5f2c: Pull complete 
831f51541d38: Pull complete 
Digest: sha256:af296b188c7b7df99ba960ca614439c99cb7cf252ed7bbc23e90cfda59092305
Status: Downloaded newer image for nginx:latest
ac4b72e14439ce4e970011512a6f89068fd4d6934536957245487bf3e8ad8717
Mohammads-MacBook-Air:~ mohammadashadali$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
ac4b72e14439        nginx               "/docker-entrypoint.…"   10 seconds ago      Up 3 seconds        0.0.0.0:8080->80/tcp   our_nginx
```

# Check the container

Check if the container is running by pasting 

localhost:8080 on the browser

We could also paste the command below in our terminal (mac)/command prompt/powershell (windows)



