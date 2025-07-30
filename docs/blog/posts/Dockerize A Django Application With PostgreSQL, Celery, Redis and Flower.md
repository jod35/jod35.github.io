---
date:
  created: 2025-07-28
authors:
    - jod35
categories:
    - programming
    - django
    - docker-compose
    - docker
    - celery
    - postgresql
tags:
    - django
    - docker-compose
    - docker
    - celery
    - postgresql
links:
    - index.md
    - blog/index.md
readtime: 5
comments: true
---

Welcome to this 5-part video series where we dive into creating a robust Django application, powered by a modern stack and containerized with Docker. We'll guide you through setting up a development environment with:

<!-- more -->

- [PostgreSQL](https://www.postgresql.org/) as the database
- [Gunicorn](https://gunicorn.org/) as the web server
- [Celery](https://docs.celeryproject.org/) for task queue management
- [Redis](https://redis.io/) as the message broker
- [Flower](https://flower.readthedocs.io/) for monitoring Celery tasks

Using [Docker Compose](https://docs.docker.com/compose/), we’ll bundle these components into a cohesive, easy-to-deploy environment. This setup simplifies development and ensures your app is ready to scale with a single command.

## Introduction And Project Set Up
In this part of our series, we introduce an easy setup process and guide you through starting the simple Django project. We create the web application component, then Dockerize it and run it as a container.

<iframe width="560" height="315" src="https://www.youtube.com/embed/vhUTpH2K7Gg?si=tMeHqYq4L28d7Bvr" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Set Up Django & PostgreSQL using Docker Compose
Next, we integrate PostgreSQL as our database and introduce Docker Compose to manage multiple containers. We’ll also preview the four additional services we’ll set up, connect to the database, create tables, and run Django migrations.

<iframe width="560" height="315" src="https://www.youtube.com/embed/oJN33PuIn6s?si=TeGCa_XMySggbQEb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Add Celery Background Tasks With Redis
Here, we add Celery for background task processing, configure it with a Redis container, and set up a dedicated Celery service to handle tasks efficiently.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymdTuVnecY4?si=YT6ngBD1T3jT0plB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Running Celery Background Tasks In Django
This part focuses on resolving minor issues from the previous section, ensuring our background tasks run smoothly.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymdTuVnecY4?si=gwLbkvhVPvs0r6Ek" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Monitor Celery Tasks With Flower
In this final part of our series, we add Flower, a monitoring dashboard for Celery tasks, which lets us track the status of Celery, view tasks, and check the results of tasks executed in the Task Queue. We also introduce [Docker Compose Watch](https://docs.docker.com/compose/how-tos/file-watch/), a tool that streamlines our development workflow by syncing changes from our host machine to the Docker file system, enabling seamless updates.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5oznWhK3pGs?si=675cozQV8nojQhIx" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Just In case you find any of my work helpful and you can support it, consider doing so over on 

- [Buy Me A Coffee](https://buymeacoffee.com/jod35)

- [Patreon](https://patreon.com/jod35)


Thanks for visiting, Happy Coding

