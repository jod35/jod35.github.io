---
title: "Advanced Alchemy - The Best Abstraction library for SQLAlchemy"
description: "Advanced Alchemy is a carefully crafted, thoroughly tested, optimized companion library for SQLAlchemy that provides repository and service layer patterns, sync/async support, and framework-agnostic integrations."
pubDate: "Jul 24 2026"
tags: ["sqlalchemy", "python", "litestar"]
heroImage: "/advanced_alchemy.webp"
---

If you've written SQLAlchemy-based applications long enough, you've probably built the same patterns over and over, repository classes, service layers, audit columns, session management, and migration setups. [Advanced Alchemy](https://advanced-alchemy.litestar.dev/) is a companion library that takes care of all that boilerplate so you don't have to. Maintained by the [Litestar Organization](https://litestar.dev/), it works with just about any Python web framework you throw at it, Litestar, FastAPI, Flask, Starlette, Sanic, you name it. <!-- more -->

## What Makes Advanced Alchemy Special

This library takes all those common patterns that backend developers end up writing from scratch every single time and packages them into something clean and well-tested. It's been around since 2023 and has grown fast, over 119 releases, 60+ contributors, and it's currently sitting at v1.11.0. The community behind it is active and the library just keeps getting better.

### Repository and Service Layer Patterns

You get async and sync repository classes with CRUD operations and bulk operations that are actually optimized. The service layer sits on top of those repositories and handles schema validation with Pydantic v2 or Msgspec, data transformation, and business logic. It's the kind of setup you'd probably write yourself anyway, so why not use one that's already battle-tested?

```python
from advanced_alchemy.repository import SQLAlchemyAsyncRepository
from advanced_alchemy.service import SQLAlchemyAsyncRepositoryService

class AuthorRepository(SQLAlchemyAsyncRepository[AuthorModel]):
    model_type = AuthorModel

class AuthorService(SQLAlchemyAsyncRepositoryService[AuthorModel]):
    repository_type = AuthorRepository
```

### Framework Integrations

If you're using Litestar, Advanced Alchemy is the official SQLAlchemy integration, so session management, dependency injection, and migration commands all work out of the box. FastAPI users get full support with async sessions managed through generator dependencies. For Flask, there's an extension that brings the same patterns into the application context. And if you're into Starlette or Sanic, there are dedicated extensions for those too. Basically, whatever framework you're on, you're covered.

### Features Worth Talking About

The library supports both sync and async, so you can pick whichever fits your style. It comes with an Alembic setup that integrates directly into your framework's CLI, so no more wrangling with migration configs. The base classes give you audit columns like created_at and updated_at, plus primary key utilities that you'd otherwise write by hand. One thing I really like is that it works with SQLModel too, you can use your SQLModel `table=True` models directly with repositories and services without any extra work.

If you're scaling across multiple databases, there's read and write replica routing built right in. It also supports Dogpile caching for queries you hit frequently, composite primary keys in the repository layer, custom column types for common patterns, and built-in pagination and filtering. It's one of those libraries where you keep discovering features that make you wonder why you were doing things the hard way.

## Installation

```bash
pip install advanced-alchemy
```

Or if you're using Litestar:

```bash
pip install litestar[sqlalchemy]
```

## Watch the Overview

There's a great walkthrough that covers the core concepts and shows Advanced Alchemy in action:

<iframe width="560" height="315" src="https://www.youtube.com/embed/JZm8yrVAyF4" title="Advanced Alchemy Overview" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Why You Should Give It a Shot

At the end of the day, Advanced Alchemy saves you from writing the same SQLAlchemy boilerplate across every project you start. The patterns are proven, the framework integrations are seamless, and the team behind it really knows the Python web ecosystem. Whether you're putting together a small API or building something larger, this library gives you the kind of abstractions you'd write yourself, except they're better tested, more complete, and already done.

Check out the [official documentation](https://advanced-alchemy.litestar.dev/), explore the [GitHub repository](https://github.com/litestar-org/advanced-alchemy), or join the [Litestar Discord](https://discord.gg/litestar) if you want to see what the community is up to.
