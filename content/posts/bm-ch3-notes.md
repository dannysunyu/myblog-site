+++
title = 'Bootstrapping Microservices第三章笔记'
date = 2025-07-04T13:21:14+07:00
draft = false
+++

A microservices application, however, isn’t a microservices application if it only consists of a single microservice!

We’d like to add a database, that’s one container, but it’s not something we consider as a microservice.

We could use the local version of Kubernetes that is included with Docker Desktop, but it’s kind of resource hungry 
(try running it on a laptop if you want to see poor performance) and just not that convenient to use when we’re working 
on multiple projects.

For now, we can “simulate” Kubernetes on our development computer using Docker Compose, which is much easier and more
straightforward than trying to dive straight into Kubernetes.

Why Docker Compose? In the same way that Docker allows us to build, run, and manage a single microservice, Docker 
Compose gives us a convenient way to build, run, and manage multiple microservices in development. During development 
and testing, we must frequently boot and reboot our entire application, which will eventually contain many 
microservices. After each small increment of development, we also must test the changes to our code.

Docker Compose revolves around the Docker Compose file. I like to think of this as a script file that builds a local 
instance of a microservices application.

The Docker Compose file is a script that specifies how to compose an application from multiple Docker containers.    

The Docker Compose file is like a script for building and launching a microservices

Recall the Dockerfile we created, which was a script for building a single image. The Docker Compose file scales this up
and allows us to orchestrate the creation of a whole application from a collection of Dockerfiles. Docker Compose reads
the Docker Compose file and produces a running application

We’re now building an application that will soon have more than one microservice. We must therefore put each 
microservice into its own separate subdirectory. Our convention is that each subdirectory will be named after its 
microservice.

Our Docker Compose file, which is called `docker-compose.yaml`. Because it doesn’t belong to any single microservice, it 
lives in the root directory of our microservices application.

```docker
services:

  video-streaming:
    image: video-streaming
    build: 
      context: ./video-streaming
      dockerfile: Dockerfile
    container_name: video-streaming
    ports:
     - "4000:8080"
    environment:
      - PORT=8080
    restart: "no"
```

You might be wondering why we set the `restart` option to no. When working in development, we don’t want our 
microservices to automatically restart when they crash. If they did that, we could easily miss problems! Instead, if 
these crash, we want them to stay that way so that we’ll notice the problem. This is the opposite of how we’d usually 
like our microservices to work in production. We’ll see later in chapter 11 how we can have Kubernetes automatically 
restart our production microservices that crash.

The output of Docker commands such as `docker ps` can be different from the output of `docker compose ps`. That’s 
because Docker commands relate to all images and containers on our development computer, whereas Docker Compose commands
only relate to the images and containers specified in our Docker Compose file.

In this sense, we’re using Docker Compose like a scoping mechanism. It constrains the commands to apply only to images 
and containers in our current project. Essentially, it restricts the scope of these commands to the current working 
directory, which is another useful aspect of Docker Compose.

Put another way, `docker compose ps` shows us only the containers that are listed in our Docker Compose file, whereas, 
`docker ps` shows us all containers on our development computer.
