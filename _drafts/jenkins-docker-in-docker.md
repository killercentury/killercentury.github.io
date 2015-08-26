---
layout: post
title:  "Jenkins Docker in Docker"
date:   2015-09-01 08:00:00
---
Since I started to play around Docker from last year, I have been attracted by the convenience it brings to the entire development and deployment workflow. A few months ago, I was going to deploy a new Jenkins server into our new infrastructure to handle a growing number of jobs for our projects.

First, I started to look at the [official Jenkins repo](https://hub.docker.com/_/jenkins/) on Docker Hub, which provides a fully functional Jenkins server via a simple docker run command. As many other official Docker images, it is trusted and well configured for most of cases. But a question comes up immediately  is that how we should build our applications. Should we pre-install everything we need inside the Jenkins server? This could mean that we need to install all the build tools and relevant runtimes manually. Obviously, I believe many of us won't be interested to do it manually and do it again and again for migration or new deployment. So how about building a new Jenkins Docker image based on the official one and including all the things we need in the Dockerfile? It seems reasonable at the beginning since it follows the infrastructure-as-code principle. But every time you need to update the build environment, you need to re-build the Docker image and re-deploy it, which is not flexible as I want.
