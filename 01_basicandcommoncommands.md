# Docker commands are the same on Linux, Mac and Windows

# Running the Container

docker run -dit debian 

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker run -dit debian
Unable to find image 'debian:latest' locally
latest: Pulling from library/debian
bd73737482dd: Pull complete 
Digest: sha256:432f545c6ba13b79e2681f4cc4858788b0ab099fc1cca799cc0fae4687c69070
Status: Downloaded newer image for debian:latest
4e02a9dce9c5e8f07f36e2b123cd87a00116771787a22ac11988b0762a019b27
```

In the above example the docker container is being run on detached mode with an interactive terminal. Here's what each option does:

* -d or --detach: This option tells Docker to run the container in the background (detached mode), 
allowing you to continue using your terminal for other tasks while the container runs.

* -i or --interactive: This option keeps the STDIN (standard input) open, 
allowing you to interact with the container's shell or command prompt.

* -t or --tty: This option allocates a pseudo-TTY (terminal) for the container, providing an interactive shell experience.
By combining these options, docker -dit allows you to start a container that runs in the background while still being able to interact with it through the terminal.

# Container ID

In the above example the last line of the output is the container id

```
4e02a9dce9c5e8f07f36e2b123cd87a00116771787a22ac11988b0762a019b27
```

# Running a container with incorrect syntax

docker run -dit debiann

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker run -dit debiann
Unable to find image 'debiann:latest' locally
docker: Error response from daemon: pull access denied for debiann, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
```

# To check what containers are running currently

docker ps
```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
4e02a9dce9c5        debian              "bash"              12 minutes ago      Up 12 minutes                           focused_chatterjee
```

# To stop a running container by the Container ID

docker stop 4e0

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker stop 4e0
4e0
```

# To stop a running container by the container name

docker stop great_ardinghelli

```
docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS              PORTS               NAMES
52c4886509e9        debian              "bash"              About a minute ago   Up About a minute                       great_ardinghelli
Mohammads-MacBook-Air:~ mohammadashadali$ docker stop great_ardinghelli
great_ardinghelli
```

# How to not run a docker container

docker run debian

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker run debian
Mohammads-MacBook-Air:~ mohammadashadali$ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
Mohammads-MacBook-Air:~ mohammadashadali$ 
```

# Other methods of running docker in detached mode

docker run -d -i -t debian

docker -it -d debian

# To check docker images that are currently present in the machine

docker images

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
debian              latest              1ac99357ef21        11 days ago         124MB
```

# To inspect the docker container

docker ps (see if any container is running through this command)

docker inspect containerid (grab the container id from above command and use it to inspect the container)

# Using the docker help command

docker --help

```

Mohammads-MacBook-Air:~ mohammadashadali$ docker --help

Usage:	docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Options:
      --config string      Location of client config files (default "/Users/mohammadashadali/.docker")
  -c, --context string     Name of the context to use to connect to the daemon (overrides DOCKER_HOST env var and default
                           context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level ("debug"|"info"|"warn"|"error"|"fatal") (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default "/Users/mohammadashadali/.docker/ca.pem")
      --tlscert string     Path to TLS certificate file (default "/Users/mohammadashadali/.docker/cert.pem")
      --tlskey string      Path to TLS key file (default "/Users/mohammadashadali/.docker/key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  builder     Manage builds
  config      Manage Docker configs
  container   Manage containers
  context     Manage contexts
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
```

# Looking up help regarding subcommands

docker images --help

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker images --help

Usage:	docker images [OPTIONS] [REPOSITORY[:TAG]]

List images

Options:
  -a, --all             Show all images (default hides intermediate images)
      --digests         Show digests
  -f, --filter filter   Filter output based on conditions provided
      --format string   Pretty-print images using a Go template
      --no-trunc        Don't truncate output
  -q, --quiet           Only show numeric IDs
```




