# Making a Container Publicly Available

# Goal:

The goal of this exercise to expose the port of a container to the outside world. For this exercise, we will use the Apache HTTP Server.

Instructions:

Start a Container Using the Apache HTTP Server Image

The image name for the Apache HTTP Server is "httpd." Start an image named "apache_welcome" using the "httpd" image. Use port 9900 on the docker host system to communicate with port 80 on the container.

 docker run --name apache_welcome -d -p 9900:80 httpd:latest
Confirm the Port is Open

Use the "​docker ps​" command and examine the "PORTS" column for your apache_welcome container.

docker ps -a
Confirm that you see "0.0.0.0:9900->80/tcp" in the "PORTS" column.

View the Application

Use the "curl" command to access Apache

 curl http://localhost:9900
You should see HTML returned.

If you are running Docker on your local system, you can further check that Apache is accessible by

typing "​http://localhost:9900​" into your web browser's address bar and hitting "Enter."
