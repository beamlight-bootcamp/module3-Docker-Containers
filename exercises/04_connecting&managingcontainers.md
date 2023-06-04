# Entering and Connecting to Containers

* Goal:

The goal of this exercise is to practice the two common ways of entering a container. The first method that you'll practice is entering the container at runtime. The second method you'll practice is entering or connecting to a container that is already running. In practice, you'll find the second method to be the one you'll use most often.

Instructions:

Enter a Container at Runtime

Launch a container based on the "redis" image and start an interactive shell. 
Name the container "enter_redis" and run the container in the foreground.

```
 docker run -it --name enter_redis redis /bin/bash
```

Because the container is running in the foreground, when the process that started the container stops, the container itself stops. 
To stop the Bash shell, type "exit".

```
exit
```

Confirm that the container stopped.

```
docker ps -a
```

You should see that the status of the "enter_redis" container is "Exited."

# Enter a Running Container

Most often, you'll want to connect to a container that is already running.

First, start a container named "exec_command_redis" based on the "redis" image. Run it in the background.

```
 docker run -dit --name exec_command_redis redis
```

Check that it’s running properly after starting it detached.

```
docker ps
```

Enter the container by running the bash shell. Remember, that you'll need the "-it" option to do.

```
docker exec -it exec_command_redis /bin/bash
```

You are presented with a prompt again. End your shell by typing "Ctrl-D" or by executing the "exit" command.

```
exit
```

Check that the container is still running:

```
docker ps
```
You should still see your container running after disconnecting from it.
