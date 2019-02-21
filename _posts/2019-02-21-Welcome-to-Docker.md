---
layout: post
title:  "Welcome To Docker"
date:   2019-02-21 12:00
categories: docker
permalink: /archivers/welcome-to-docker
---

Welcome to Docker

![](https://www.maketecheasier.com/assets/uploads/2019/01/docker-featured-400x200.jpg)

**This chapter covers**
- [What is Docker](#what-is-docker)
- [An introduction to containers](#an-in-troduction-to-containers)
- [How Docker addresses software problems that most people tolerate](#how-docker-address-software-problems-that-most-people-tolerate)
- [When, where, and why you should use Docker](#when-where-and-why-you-should-use-docker)
- [Example: “Hello, World”](#example)

# 1. What is Docker?

Docker is a command-line program, a background daemon, and a set of remote services that take a logistical approach to solving common software problems and simpli- fying your experience installing, running, publishing, and removing software. It accomplishes this using a UNIX technology called containers.

## 1.1 Containers

Using containers has been a best practice for a long time. But manually building containers can be challenging and easy to do incorrectly. This challenge has put them out of reach for some, and misconfigured containers have lulled others into a false sense of security. We need a solution to this problem, and Docker helps. Any software run with Docker is run inside a container. Docker uses existing container engines to provide consistent containers built according to best practices. This puts stronger security within reach for everyone.

With Docker, users get containers at a much lower cost. As Docker and its container engines improve, you get the latest and greatest jail features. Instead of keeping up with the rapidly evolving and highly technical world of building strong application jails, you can let Docker handle the bulk of that for you. This will save you a lot of time and money and bring peace of mind.

## 1.2 Containers are not virtualization

Unlike virtual machines, Docker containers don’t use hardware virtualization. Programs running inside Docker containers interface directly with the host’s Linux kernel. Because there’s no additional layer between the program running inside the container and the computer’s operating system, no resources are wasted by running redundant software or simulating virtual hardware. This is an important distinction. Docker is not a virtualization technology. Instead, it helps you use the container technology already built into your operating system.

## 1.3 Running software in containers for isolation

As noted earlier, containers have existed for decades. Docker uses Linux namespaces and cgroups, which have been part of Linux since 2007. Docker doesn’t provide the container technology, but it specifically makes it simpler to use. To understand what containers look like on a system, let’s first establish a baseline. Figure 1.1 shows a basic example running on a simplified computer system architecture.
Notice that the command-line interface, or CLI, runs in what is called user space memory just like other programs that run on top of the operating system. Ideally,

![](https://user-images.githubusercontent.com/10813839/53149713-1489ce00-35e1-11e9-8fd3-62c9c666c740.png)

![](https://user-images.githubusercontent.com/10813839/53151652-5406e900-35e6-11e9-88b9-7ab124fd0a04.png)

programs running in user space can’t modify kernel space memory. Broadly speaking, the operating system is the interface between all user programs and the hardware that the computer is running on.
You can see in figure 1.2 that running Docker means running two programs in user space. The first is the Docker daemon. If installed properly, this process should always be running. The second is the Docker CLI. This is the Docker program that users interact with. If you want to start, stop, or install software, you’ll issue a com- mand using the Docker program.

Figure 1.2 also shows three running containers. Each is running as a child process of the Docker daemon, wrapped with a container, and the delegate process is running in its own memory subspace of the user space. Programs running inside a container can access only their own memory and resources as scoped by the container.
The containers that Docker builds are isolated with respect to eight aspects. Part 1 of this book covers each of these aspects through an exploration of Docker container features. The specific aspects are as follows:

- **PID** namespace—Process identifiers and capabilities
- **UTS** namespace—Host and domain name
- **MNT** namespace—File system access and structure
- **IPC** namespace—Process communication over shared memory
- **NET** namespace—Network access and structure
- **USR** namespace—User names and identifiers
- **chroot()—Controls** the location of the file system root
- **cgroups—Resource** protection

Linux namespaces and cgroups take care of containers at runtime. Docker uses another set of technologies to provide containers for files that act like shipping containers.

## 1.4 Shipping containers

Docker provides a set of infrastructure components that simplify distributing Docker images. These components are registries and indexes. You can use publicly avail- able infrastructure provided by Docker Inc., other hosting companies, or your own registries and indexes.

# 2. What problems does Docker solve?

Using software is complex. Before installation you have to consider what operating system you’re using, the resources the software requires, what other software is already installed, and what other software it depends on. You need to decide where it should be installed. Then you need to know how to install it. It’s surprising how drastically installation processes vary today. The list of considerations is long and unforgiving. Installing software is at best inconsistent and overcomplicated.

Most computers have more than one application installed and running. And most applications have dependencies on other software. What happens when two or more applications you want to use don’t play well together? Disaster. Things are only made more complicated when two or more applications share dependencies:

- What happens if one application needs an upgraded dependency but the other does not?
- What happens when you remove an application? Is it really gone?
- Can you remove old dependencies?
- Can you remember all the changes you had to make to install the software you now want to remove?

The simple truth is that the more software you use, the more difficult it is to manage. Even if you can spend the time and energy required to figure out installing and running applications, how confident can you be about your security? Open and closed source programs release security updates continually, and being aware of all of the issues is often impossible. The more software you run, the greater the risk that it’s vulnerable to attack.

All of these issues can be solved with careful accounting, management of resources, and logistics, but those are mundane and unpleasant things to deal with. Your time would be better spent using the software that you’re trying to install, upgrade, or publish. The people who built Docker recognized that, and thanks to their hard work you can breeze through the solutions with minimal effort in almost no time at all.

It’s possible that most of these issues seem acceptable today. Maybe they feel trivial because you’re used to them. After reading how Docker makes these issues approachable, you may notice a shift in your opinion

# 3. Why is Docker important?

This is also the case for application removal. When you want to remove software, you simply tell Docker which software to remove. No lingering artifacts will remain because they were all carefully contained and accounted for. Your computer will be as clean as it was before you installed the software.

The container abstraction and the tools Docker provides for working with containers will change the system administration and software development landscape. Docker is important because it makes containers available to everyone. Using it saves time, money, and energy.

The second reason Docker is important is that there is significant push in the software community to adopt containers and Docker. This push is so strong that companies like Amazon, Microsoft, and Google have all worked together to contribute to its development and adopt it in their own cloud offerings. These companies, which are typically at odds, have come together to support an open source project instead of developing and releasing their own solutions.

The third reason Docker is important is that it has accomplished for the computer what app stores did for mobile devices. It has made software installation, compartmen talization, and removal very simple. Better yet, Docker does it in a cross-platform and open way. Imagine if all of the major smartphones shared the same app store. That would be a pretty big deal. It’s possible with this technology in place that the lines between operating systems may finally start to blur, and third-party offerings will be less of a factor in choosing an operating system.

Fourth, we’re finally starting to see better adoption of some of the more advanced isolation features of operating systems. This may seem minor, but quite a few people are trying to make computers more secure through isolation at the operating system level. It’s been a shame that their hard work has taken so long to see mass adoption. Containers have existed for decades in one form or another. It’s great that Docker helps us take advantage of those features without all the complexity.

# 4. Where and when to use Docker

Docker can run almost anywhere, but that doesn’t mean you’ll want to do so. For example, currently Docker can only run applications that can run on a Linux operating system. This means that if you want to run an OS X or Windows native application, you can’t yet do so through Docker.

# 5. Example: “Hello, World”

I like to get people started with an example. In keeping with tradition, we’ll use “Hello, World.” Before you begin, download and install Docker for your system. 
Detailed instructions are kept up-to-date for every available system at https://docs.docker.com/ installation/. 
OS X and Windows users will install the full Docker suite of applications using the Docker Toolbox. Once you have Docker installed and an active internet con- nection, head to your command prompt and type the following:

`docker run dockerinaction/hello_world`

After you do so, Docker will spring to life. It will start downloading various compo- nents and eventually print out “hello world.” If you run it again, it will just print out “hello world.” Several things are happening in this example, and the command itself has a few distinct parts.

![](https://user-images.githubusercontent.com/10813839/53154192-cbd81200-35ec-11e9-811d-28da1e7aaf9f.png)

First, you use the docker run command to start a new container. This single com- mand triggers a sequence (shown in figure 1.6) that installs, runs, and stops a pro- gram inside a container.
Second, the program that you tell it to run in a container is dockerinaction/ hello_world. This is called the repository (or image) name. For now, you can think of the repository name as the name of the program you want to install or run.

# 6. Summary

This chapter has been a brief introduction to Docker and the problems it helps system administrators, developers, and other software users solve. In this chapter you learned that:
- Docker takes a logistical approach to solving common software problems and simplifies your experience with installing, running, publishing, and removing software. It’s a command-line program, a background daemon, and a set of remote services. It’s integrated with community tools provided by Docker Inc.
- The container abstraction is at the core of its logistical approach.
- Working with containers instead of software creates a consistent interface and enables the development of more sophisticated tools.
- Containers help keep your computers tidy because software inside containers
can’t interact with anything outside those containers, and no shared dependencies can be formed.
- Because Docker is available and supported on Linux, OS X, and Windows, most software packaged in Docker images can be used on any computer.
- Docker doesn’t provide container technology; it hides the complexity of working directly with the container software.

