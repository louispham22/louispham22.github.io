---
layout: post
title:  "600k concurrent websocket connections on AWS using Node.js"
date:   2019-03-18 14:30
categories: nodejs
permalink: /archivers/600k-concurrent-websocket-connections-on-AWS-using-Node.js
---

# 600k concurrent websocket connections on AWS using Node.js

I recently faced the challenge to get as much power as possible out of a AWS EC2 instance at the lowest possible cost using concurrent persistent websockets.

To do this I needed to use a event-driven, non-blocking runtime environment. For this particular purpose Node.js is excellent with its lightweight and fast Chrome V8 engine.

# Technical decisions

## Socket.io

I started out with using Socket.io for Node.js which worked out nicely as a start but since we are trying to get as much as possible out of the EC2 instance we needed something that is a little bit more light-weight. Also I noticed that since Socket.io v1.0 the cluster module doesn’t work. This removes the possibility to use this library on a environment with high load. Therefore I moved on to another websocket library Websockets/ws.

## Websockets/ws

Works good and is lightweight. This is probably the fastest Websocket library for Node.js. The library has no built in keep alive functionality so you have to implement that yourself via the ping/methods available in the lib. Make sure that your AWS loadbalancers timeout is not set lower than your keepalive, if not, it will drop your connections.

## Sticky-session

Use the sticky-session Node.js module which enables you to run on all CPUs. Which you have to do in order to reach a high number of connections for one server. One CPU can only handle a certain amount of connections before the V8 GC goes wild and the CPU will stall on 100%.

## M3.xlarge

After a lot of testing by generating users to create persistent websocket connections to the server and calculating the numbers up and down I finally decided to use a M3.xlarge EC2 instance to reach 620k idle connections. This gives us 4 CPUs and 15Gb of memory.

At this level of live persistent connections the CPU load is constantly at 100% on all CPUs on the server. The reason behind the high CPU load is the V8:s(Node.js engine) garbage collection. But this is after optimizing the GC. To have a stable runtime environment I suggest that you set the maximum connections to 600k before the CPU load starts to go crazy high, when reaching this connection amount it is definitely time to scale up another instance.

It is possible to reach a higher number of connections on a larger and more expensive EC2 instance that provides more CPU cores and more memory. When experimenting with this I reached 800k idle connections with a M3.2xlarge instance which gives you 8 CPUs and 30Gb of memory. But when you get over 600k connections other factors comes to limit the capacity, like money and the linux network implementation.

These numbers are for idle websocket connections handling only keepalive pings from the server.  I’m sure if you have a high number of requests from the clients, the number of connections that the EC2 instance can handle will also decrease.

 

# Configuration to reach 600k persistent connections

## Node.js flags

Set the following flags to launch your node.js application:


`node --nouse-idle-notification--expose-gc--max-new-space-size=2048--max-old-space-size=8192 ./server/websocketserver.js
–nouse-idle-notification`

Turns of the idle garbage collection which makes the GC constantly run and is devastating for a realtime server environment. If not turned off the system will get a long hickup for almost a second once every few seconds.

`–expose-gc`

Use the expose-gc command to enable manual control of the GC from your code. I recommend to call GC once every 30 seconds.

`–max-old-space-size=8192`

Increases the limit for each V8 node process to use max 8Gb of heap memory instead of the 1,4Gb default on 64-bit machines(512Mb on a 32-bit machine).

`–max-new-space-size=2048`

Specified in kb and setting this flag optimizes the V8 for a stable allround environment with short pauses and ok high peak performance.

If this flag is not used the pauses will be a little bit longer but the machine will handle peaks a little bit better. What you need in this case depends on the project you are working on. My pick is to have an allround stable server instead of just handling peaks so I stick with this flag.

EC2 configuration

Set the “soft” and “hard” nofile limit to 1000000. Instead of using the “ulimit -n” as some people do I had to specify the “soft” and “hard” limits for both root and all other users, for some reason I had to specify them separately.

/etc/security/limits.d/custom.conf


```sh
root soft nofile 1000000
root hard nofile 1000000
* soft nofile 1000000
* hard nofile 1000000
```
Now set the amount of possible opened file handles and the size of the NAT ip connection tracking table.

/etc/sysctl.conf

```sh
 fs.file-max = 1000000
 fs.nr_open = 1000000       
 net.ipv4.netfilter.ip_conntrack_max = 1048576
 net.nf_conntrack_max = 1048576
```

`“fs.file-max”`

The maximum file handles that can be allocated

`“fs.nr_open”`

Max amount of file handles that can be opened

`“net.ipv4.netfilter.ip_conntrack_max”`

Specifies how many connections the NAT can keep track of in the “tracking” table before it starts to drop packets and just break connections, this we totally want to avoid. The default value for this is 65536 so without this setting you wont be able to get more connections than that.