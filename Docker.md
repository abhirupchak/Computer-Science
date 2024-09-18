# Docker Cheat Sheet

A quick reference guide to Docker commands, tags, and basic usage. This document will help you get started with Docker, manage images and containers, and create your own Docker images.

---

## Table of Contents
1. [What is Docker?](#what-is-docker)
2. [Docker Hub](#docker-hub)
3. [Docker Images](#docker-images)
4. [Common Docker Commands](#common-docker-commands)
5. [Docker Tags](#docker-tags)
6. [Creating Your Own Docker Image](#creating-your-own-docker-image)
7. [Environmental Variables](#environmental-variables)

---

## What is Docker?

Docker is a platform that allows you to automate the deployment of applications inside lightweight, portable containers. It helps developers ship their code faster, ensuring that it runs the same on every system.

---

## Docker Hub

Docker Hub is a cloud-based registry where Docker images are stored. You can find pre-built images for various applications or upload your own.

**Useful commands for Docker Hub:**
- docker pull <image_name>: Pulls an image from Docker Hub.

---

## Docker Images

A Docker image is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including code, runtime, libraries, and environment variables.

**Docker Image Commands:**
- docker images: Lists all Docker images on your system.
- docker pull <image_name>: Downloads a Docker image from Docker Hub.
- docker rmi <image_id>: Removes a specific Docker image from your system.

---

## Common Docker Commands

1. **Run a Container:**
   docker run [options] <image_name>

   Options:
   - -d: Run the container in detached mode.
   - -p: Publish a container’s port to the host (e.g., -p 8080:80).
   - --name: Assign a name to the container.
   - -v: Mount volumes from the host to the container.
   - -e: Set environment variables.
   - -i: Run the container in interactive mode.
   - -t: Allocate a pseudo-TTY.

2. **Exec into a Running Container:**
   docker exec -it <container_name> /bin/bash

3. **List Running Containers:**
   docker ps

4. **Inspect a Container:**
   docker inspect <container_name>

5. **Stop and Remove Containers:**
   docker stop <container_name>
   docker rm <container_name>

6. **Remove an Image:**
   docker rmi <image_name>

---

## Docker Tags

Tags are used to identify different versions of a Docker image.

**Common Tags:**
- -p: Publish ports.
- -v: Mount volumes.
- -t: Allocate a pseudo-TTY.
- -i: Keep STDIN open even if not attached.
- -e: Set environment variables.
- -d: Run in detached mode.
- -a: Attach to the container's STDOUT.

---

## Creating Your Own Docker Image

To create your own Docker image, you need a Dockerfile. A Dockerfile contains a series of instructions for Docker to build the image.

1. **Create a Dockerfile:**

   FROM ubuntu:latest
   
   ENV APP_HOME /app
   
   RUN mkdir $APP_HOME
   
   COPY . $APP_HOME
   
   WORKDIR $APP_HOME
   
   CMD ["python", "app.py"]

2. **Build the Docker Image:**
   docker build -t myapp .

3. **Run the Image as a Container:**
   docker run -d -p 5000:5000 --name myapp_container myapp

---

## Environmental Variables

Environmental variables can be passed to containers using the -e flag in the docker run command.

**Example:**
docker run -e VAR_NAME=value -d <image_name>

In Dockerfiles, you can also define environment variables using the ENV instruction:

   ENV VAR_NAME=value
