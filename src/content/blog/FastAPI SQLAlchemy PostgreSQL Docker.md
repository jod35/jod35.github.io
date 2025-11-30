---
title: "Building a FastAPI Application with PostgreSQL, SQLAlchemy and Alembic, and Docker"
description: "Setting up a robust development environment for modern web applications can be complex, but with the right tools and approach, it becomes manageable and efficient."
pubDate: "Nov 30 2025"
tags: ["fastapi", "sqlalchemy", "alembic", "uv","postgresql"]
---


<iframe width="560" height="315" src="https://www.youtube.com/embed/JWQEostzy60?si=xvU3HOX7-jdgcZiv" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

Creating a development environment for modern web applications can be complex, but with the right tools and approach, it becomes manageable and efficient. In this guide, we'll explore how to create a complete FastAPI application stack using PostgreSQL, SQLAlchemy, Alembic, and Docker.

## What You'll Learn

By the end of this tutorial, you'll have a fully functional development environment that includes:

- A FastAPI application with modern Python async capabilities
- PostgreSQL database with persistent data storage
- SQLAlchemy 2.0 ORM with async support
- Alembic for seamless database migrations
- Docker containerization for consistent environments
- Hot-reloading for efficient development workflow

## Project Overview

We'll build our application using a containerized approach where each service runs in its own Docker container, managed through Docker Compose. This setup ensures consistency across different development environments and makes deployment straightforward.

### Key Technologies

- **FastAPI**: A modern, fast web framework for building APIs with Python
- **PostgreSQL**: A powerful, open-source relational database
- **SQLAlchemy 2.0**: The latest version of Python's most popular ORM
- **Alembic**: Database migration tool for SQLAlchemy
- **Docker & Docker Compose**: Containerization and orchestration

## Step-by-Step Implementation

### Project Structure Setup

First, we'll organize our project with a clean, maintainable structure that separates concerns and follows Python best practices.

### FastAPI Dockerfile Configuration

We'll create a Dockerfile that leverages Python's latest features while keeping the container lightweight and secure.

### PostgreSQL Database Setup

Our PostgreSQL configuration will include persistent volume mapping to ensure data survives container restarts and updates.

### SQLAlchemy 2.0 Integration

We'll implement the modern SQLAlchemy 2.0 syntax with async support, taking advantage of Python's asyncio capabilities for better performance.

### Alembic Migration Management

Database schema changes will be handled through Alembic migrations, providing version control for your database structure.

### Docker Compose Orchestration

Finally, we'll tie everything together with Docker Compose, enabling you to start your entire development stack with a single command.

### Development Workflow

The setup includes hot-reloading capabilities, allowing you to see changes instantly without manual container restarts. This is achieved using Docker Compose Watch.

## Benefits of This Approach

- **Consistency**: Docker ensures your app runs the same everywhere
- **Scalability**: Easy to add new services or scale existing ones
- **Maintainability**: Clear separation of concerns and modern tooling
- **Performance**: Async support throughout the stack
- **Developer Experience**: Hot-reloading and easy setup commands

You can fund the source [here](https://github.com/jod35/fastapi-postgresql-sqlalchemy-alembic-docker-template). 