# Registries

- Dockerhub is the default registry
- The primary function the registry is to hold/store images
- A repository is a collection of images
- Each image is stored as a tag

Example:

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker pull docker.io/ubuntu:bionic
bionic: Pulling from library/ubuntu
7c457f213c76: Pull complete 
Digest: sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e43c98
Status: Downloaded newer image for ubuntu:bionic
docker.io/library/ubuntu:bionic
```

We can accomplish the same thing by doing 
```
docker pull ubuntu:bionic
```

Another example:

```
docker pull registry.hub.docker.com/library/ubuntu:bionic
```

Lets check out local images:

```
docker images
```

Sample output:

```
Mohammads-MacBook-Air:~ mohammadashadali$ docker pull registry.hub.docker.com/library/ubuntu:bionic
bionic: Pulling from library/ubuntu
Digest: sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e43c98
Status: Downloaded newer image for registry.hub.docker.com/library/ubuntu:bionic
registry.hub.docker.com/library/ubuntu:bionic
Mohammads-MacBook-Air:~ mohammadashadali$ docker images
REPOSITORY                               TAG                 IMAGE ID            CREATED             SIZE
ubuntu                                   bionic              f9a80a55f492        5 days ago          63.2MB
registry.hub.docker.com/library/ubuntu   bionic              f9a80a55f492        5 days ago          63.2MB
```

If we want to start any of these containers we have to give the full name

example:

```
docker run -dit registry.hub.docker.com/library/ubuntu:bionic
```

# Image Repository

In order to understand image repository lets look at the command below:

```
docker pull mysql/mysql-server
```

In the above example mysql is a repository & mysql-server is the image & we know from previous lectures
is that when we dont specify any tags by default latest tage is used. If we go to dockerhub & search
by mysql/, we will see other images that are available within the mysql repository.

# Other container registry

In addition to dockerhub there are other popular container registries, below are some

Amazon - ECR (which stands for elastic container registry)
Redhat- Quay
Google - GCR (Stands for google container registry)

Many companies might have their own private registries.



