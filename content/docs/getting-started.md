---
title: Getting started
date: 2023-11-05T17:40:05Z
draft: false
---

This section describes how to get an instance of Yeti up and running in no time.
Executed on a server, it will open a port on http://0.0.0.0:80/.

## Prerequisites

The supported install method for Yeti is using its dedicated Docker containers.
To install Yeti, you need to have the following tools installed on your system:

- git
- Docker

## Starting docker containers

```bash
git clone https://github.com/yeti-platform/yeti-docker
cd yeti-docker/prod
docker compose up
```

This should get Yeti up and running on port http://localhost:80/. The docker
compose file starts up 4 containers:

- `api` - The API server, where most of the Yeti system runs; ()
- `frontend` - the web frontend, served by nginx; ()
- `tasks` - a Celery scheduler;
- `redis` - a Redis server;
- `arangodb` - an ArangoDB server.

It will also create a Docker network called `yeti_network` through which all
containers can talk to one another.

## Create an admin user

You'll need to create an admin user to be able to log into the Yeti web
interface:

```bash
docker compose exec api yetictl create-user USERNAME PASSWORD --admin
```