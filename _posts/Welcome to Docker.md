---
layout: post
title:  "Style Test"
date:   1970-01-01 08:00
categories: jekyll
permalink: /archivers/test
---

Welcome to Docker

![](https://www.maketecheasier.com/assets/uploads/2019/01/docker-featured-400x200.jpg)

This chapter covers
■ What Docker is
■ An introduction to containers
■ How Docker addresses software problems that most people tolerate
■ When, where, and why you should use Docker
■ Example: “Hello, World”

# What is Docker?

Docker is a command-line program, a background daemon, and a set of remote ser- vices that take a logistical approach to solving common software problems and simpli- fying your experience installing, running, publishing, and removing software. It accomplishes this using a UNIX technology called containers.

## Containers

Historically, UNIX-style operating systems have used the term jail to describe a modi- fied runtime environment for a program that prevents that program from accessing protected resources. Since 2005, after the release of Sun’s Solaris 10 and Solaris Con- tainers, container has become the preferred term for such a runtime environment. The goal has expanded from preventing access to protected resources to isolating a pro- cess from all resources except where explicitly allowed.
Using containers has been a best practice for a long time. But manually building containers can be challenging and easy to do incorrectly. This challenge has put them out of reach for some, and misconfigured containers have lulled others into a false sense of security. We need a solution to this problem, and Docker helps. Any software run with Docker is run inside a container. Docker uses existing container engines to provide consistent containers built according to best practices. This puts stronger security within reach for everyone.
With Docker, users get containers at a much lower cost. As Docker and its con- tainer engines improve, you get the latest and greatest jail features. Instead of keeping up with the rapidly evolving and highly technical world of building strong application jails, you can let Docker handle the bulk of that for you. This will save you a lot of time and money and bring peace of mind.

## Containers are not virtualization

Without Docker, businesses typically use hardware virtualization (also known as virtual machines) to provide isolation. Virtual machines provide virtual hardware on which an operating system and other programs can be installed. They take a long time (often minutes) to create and require significant resource overhead because they run a whole copy of an operating system in addition to the software you want to use.
Unlike virtual machines, Docker containers don’t use hardware virtualization. Pro- grams running inside Docker containers interface directly with the host’s Linux ker- nel. Because there’s no additional layer between the program running inside the container and the computer’s operating system, no resources are wasted by running redundant software or simulating virtual hardware. This is an important distinction. Docker is not a virtualization technology. Instead, it helps you use the container tech- nology already built into your operating system.

## Running software in containers for isolation

As noted earlier, containers have existed for decades. Docker uses Linux namespaces and cgroups, which have been part of Linux since 2007. Docker doesn’t provide the container technology, but it specifically makes it simpler to use. To understand what containers look like on a system, let’s first establish a baseline. Figure 1.1 shows a basic example running on a simplified computer system architecture.
Notice that the command-line interface, or CLI, runs in what is called user space memory just like other programs that run on top of the operating system. Ideally,

![](http://prntscr.com/mnz5u2)