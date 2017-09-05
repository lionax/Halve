---
layout: post
title:  "StarCraft Broodwar in a Docker-Container!"
date:   2017-09-05
excerpt: "Run your StarCraft Broodwar on any operating system."
tag:
- starcraft 
- tensorflow
- docker
- ml
---

<b>lionax/docker-starcraft</b> is a docker image aimed for the execution of BWAPI bots on any operating system that supports docker.

I created the image for two purposes:

* to be able to run StarCraft and BWAPI bots on Linux
* to apply Machine Learning to BWAPI bots in a Linux environment with Python and TensorFlow

Currently I'm working on an integration of [Machine Learning](https://en.wikipedia.org/wiki/Machine_learning) techniques for Strategy Generation into StarCraft Broodwar API bots. For this purpose I asked myself if it was possible to run StarCraft and the API in a docker container on linux making the environment portable.

Checkout the current status of the project on [Docker Hub](https://hub.docker.com/r/lionax/docker-starcraft/) and [Github](https://github.com/lionax/docker-starcraft).

## Several problems to solve

As for the more interesting problems to tackle I had to start an x-session within one of the image layers in order to properly initialize the wine prefix.

I extracted the contents of the [BWAPI 4.1.2 installer](https://github.com/bwapi/bwapi/releases/tag/v4.1.2) and placed them into my own [BWAPI repository](https://github.com/lionax/bwapi/releases/tag/v4.1.2). This enables an unattended installation into the image.

*Side-note: because of the size of the image and the fact that I used aufs as docker storage driver my disk-space ran out of space (o bytes left) and some of my data was destroyed (see [this stackexchange](https://stackoverflow.com/questions/27853571/why-is-docker-image-eating-up-my-disk-space-that-is-not-used-by-docker/27894675#27894675)). I removed docker completely and switched to overlay2, hoping that the problem will be solved.*

## Part of a bigger picture

This project is part of my whole bachelor thesis and bot-development project called 'odysseus', which at the moment is not open to the public though.

Related to this project and my bachelor thesis in general:

* [Docker-BotCraft](https://hub.docker.com/r/lionax/docker-botcraft/) - A cross-compile environment backed with docker.
* [BOSS](https://hub.docker.com/r/lionax/docker-botcraft/) - The Build Order Search System of the [UAlbertaBot](https://github.com/davechurchill/ualbertabot) as separate project with some modifications and cross-compilation support.
* Odysseus - A bot utilizing machine learning for strategy generation. *Not published yet*