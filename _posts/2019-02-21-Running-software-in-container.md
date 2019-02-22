---
layout: post
title:  "Running software in containers"
date:   2019-02-10 15:30
categories: docker
permalink: /archivers/running-sotfware-in-containers
---

Running software in containers

**This chapter covers**

- Running interactive and daemon terminal programs with containers
- Containers and the PID namespace
- Container configuration and output
- Running multiple programs in a container
- Injecting configuration into containers
- Durable containers and the container life cycle
- Cleaning up

# 1. Getting help with the Docker command line

You’ll use the docker command-line program throughout the rest of this book. To get you started with that, I want to show you how to get information about commands from the docker program itself. This way you’ll understand how to use the exact version of Docker on your computer. Open a terminal, or command prompt, and run the following command:

`docker help`

# 2. Controlling containers: building a website monitor

In this first example, you’re going to install a web server called NGINX.

![](https://user-images.githubusercontent.com/10813839/53154941-80266800-35ee-11e9-9d0f-2c7a7fc0e961.png)

## 2.1 Creating and starting a new container

Running the following command will download, install, and start a container running NGINX:

![](https://user-images.githubusercontent.com/10813839/53155040-c976b780-35ee-11e9-9b9d-358106fda5a4.png)

When you run this command, Docker will install nginx:latest from the NGINX repository hosted on Docker Hub and run the software. After Docker has installed and started running NGINX, one line of seemingly random characters will be written to the terminal. It will look something like this:

`7cb5d2b9a7eab87f07182b5bf58936c9947890995b1b94f412912fa822a9ecb5`

- **Note**: That's because you used the --detach option and started the program in the background. Remember to use either the --detach flag or its short form, -d.

The following command will install and run a mailer that will work for this example:

![](https://user-images.githubusercontent.com/10813839/53155233-35592000-35ef-11e9-92cf-5de0b3fab7b1.png)

## 2.2. Running interactive containers

To get started working with interactive containers, run the following command:

![](https://user-images.githubusercontent.com/10813839/53155301-5cafed00-35ef-11e9-8d38-d613a5e51380.png)

The command uses two flags on the run command: *--interactive (or -i) and –-tty (or –t)*. First, the *--interactive* option tells Docker to keep the standard input stream (stdin) open for the container even if no terminal is attached. Second, the *--tty* option tells Docker to allocate a virtual terminal for the container, which will allow you to pass signals to the container.

To finish the work for your client, you need to start an agent. This is a monitoring agent that will test the web server as you did in the last example and send a message with the mailer if the web server stops. This command will start the agent in an interactive container using the short-form flags:

![](https://user-images.githubusercontent.com/10813839/53155456-b0223b00-35ef-11e9-832d-5c915fd77c8f.png)

When running, the container will test the web container every second and print a message like the following:

`System up.`

## 2.3 Listing, stopping, restarting, and viewing output of containers

The first thing you should do to test your current setup is check which containers are currently running by using the docker ps command:

`docker ps`

Running the command will display the following information about each running container:

- The container ID
- The image used
- The command executed in the container
- The time since the container was created
- The duration that the container has been running
- The network ports exposed by the container
- The name of the container

