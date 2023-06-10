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

# Dockerfile

A Dockerfile is a text file that contains a set of instructions used to build a Docker image. It serves as a blueprint or recipe for creating a containerized application. Dockerfiles are a fundamental part of Docker, a popular containerization platform.

Here's a brief explanation of what a Dockerfile is and why it is used:

1. Definition: A Dockerfile is a plain-text file that typically starts with a base image and contains a series of instructions to define the steps required to create a Docker image. Each instruction represents a specific action, such as copying files, installing dependencies, or exposing ports.

2. Purpose: The primary purpose of a Dockerfile is to automate the process of building Docker images. It provides a standardized and reproducible way to package applications and their dependencies into portable, lightweight, and isolated containers. Dockerfiles capture the entire configuration and setup of an application, making it easier to deploy and run consistently across different environments.

3. Benefits:
   - Reproducibility: Dockerfiles ensure that the same Docker image can be rebuilt consistently, even on different machines or by different users. This helps eliminate discrepancies between development, testing, and production environments.
   - Version Control: Dockerfiles can be version-controlled alongside source code, enabling easy tracking of changes and collaboration among team members. This ensures that the image creation process is well-documented and easily auditable.
   - Automation: Dockerfiles allow for automated builds, making it easier to incorporate them into continuous integration and deployment pipelines. This streamlines the development and deployment workflow by reducing manual steps and increasing efficiency.
   - Modularity: Dockerfiles support a modular approach to building images, allowing you to separate different components or layers of your application. This promotes reusability and simplifies maintenance and updates.

In summary, a Dockerfile is a text-based configuration file used to automate the process of creating Docker images. It provides a declarative and reproducible way to define the environment and dependencies of an application, enabling easy packaging and deployment of containerized applications. Dockerfiles are a key component of the Docker ecosystem and facilitate efficient and consistent containerization practices.

# Dockerfile Instructions

Certainly! Here are some common instructions in a Dockerfile along with their explanations:

1. `FROM`: Specifies the base image to build upon. It is typically the first instruction in a Dockerfile. For example, `FROM python:3.8` sets the base image as the official Python 3.8 image.

2. `RUN`: Executes a command inside the container during the build process. It is used to install packages, run build scripts, or perform any other necessary setup steps. For example, `RUN apt-get update && apt-get install -y curl` updates the package repositories and installs curl.

3. `COPY` and `ADD`: Copies files from the host machine to the container's filesystem. `COPY` is used for copying local files or directories, while `ADD` allows additional features such as URL retrieval and automatic extraction of compressed files. For example, `COPY app.py /app/` copies the `app.py` file from the host to the `/app/` directory in the container.

4. `WORKDIR`: Sets the working directory for subsequent instructions in the Dockerfile. It is used to provide a relative path for other instructions like `RUN`, `COPY`, and `CMD`. For example, `WORKDIR /app` sets the working directory as `/app`.

5. `EXPOSE`: Informs Docker that the container listens on specified network ports at runtime. It does not actually publish the ports. It serves as documentation for the intended network ports to be exposed. For example, `EXPOSE 8080` indicates that the container listens on port 8080.

6. `CMD`: Specifies the default command to run when the container starts. It provides the main purpose of the container and can include command-line arguments. If the `CMD` is overridden at runtime, the provided command will be executed instead. For example, `CMD ["python", "app.py"]` sets the default command as `python app.py`.

7. `ENTRYPOINT`: Similar to `CMD`, it specifies the command to run when the container starts. However, unlike `CMD`, the `ENTRYPOINT` command is not overridden by the command provided at runtime. It becomes the entry point or "entry function" of the container. For example, `ENTRYPOINT ["python", "app.py"]` sets the entry point as `python app.py`.

8. `ENV`: Sets environment variables inside the container. It is used to provide configuration options or runtime parameters to the application. For example, `ENV API_KEY=123456` sets an environment variable `API_KEY` with the value `123456`.

These are just a few commonly used instructions in a Dockerfile. There are additional instructions available, such as `LABEL`, `USER`, `VOLUME`, and `ARG`, which provide more advanced functionality for building Docker images. The choice and usage of instructions depend on the specific requirements and configuration of your containerized application.

