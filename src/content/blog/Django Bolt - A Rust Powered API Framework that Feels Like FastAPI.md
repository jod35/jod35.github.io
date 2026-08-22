---
title: "Django Bolt - A Rust Powered API Framework that Feels Like FastAPI"
description: "Django Bolt is a high-performance API framework for Django with Rust-powered endpoints achieving 188k+ RPS. Uses Actix Web, PyO3, and msgspec for blazing-fast performance."
pubDate: "Jul 24 2026"
tags: ["django", "python", "rust", "api"]
heroImage: "/bolt.jpg"
---

Django Bolt is something I have been keeping an eye on for a while. It is a high performance API framework for Django that gives you FastAPI style decorator based routing, but the entire HTTP layer runs in Rust. Under the hood it uses Actix Web for HTTP, PyO3 to bridge Rust and Python, and msgspec for serialization. The result is a framework that can push 60k requests per second on a plain endpoint while keeping your Django ORM, Django Admin, and all your Django packages intact. <!-- more -->

## A Quick Look

The API feels familiar if you have used FastAPI or Litestar. You create a `BoltAPI` instance and use decorators to define routes:

```python
from django_bolt import BoltAPI
import msgspec

api = BoltAPI()

class CreateUser(msgspec.Struct):
    username: str
    email: str

@api.get("/users/{user_id}")
async def get_user(user_id: int):
    user = await User.objects.aget(pk=user_id)
    return {"id": user.id, "username": user.username}

@api.post("/users")
async def create_user(user: CreateUser):
    return {"username": user.username}
```

You add `django_bolt` to your `INSTALLED_APPS` and run it with a single command. No gunicorn, no uvicorn, no workers config. The Rust binary owns the socket directly.

```bash
python manage.py runbolt --dev
```

You also get automatic OpenAPI docs at `/docs` with Swagger, Redoc, Scalar, and RapiDoc all available out of the box.

## What You Get

The framework comes with a lot built in. Authentication with JWT and API keys that validate in Rust before your handler runs. Permission guards like `IsAuthenticated` that work similarly to DRF. CORS, rate limiting, and compression middleware. Class based views with ViewSet and ModelViewSet patterns if you prefer that style. Full async Django ORM support using `aget`, `afilter`, and friends. OpenAPI documentation generated automatically from your type hints. Streaming responses, Server Sent Events, file uploads and downloads, and WebSocket support. There is even an optional `bolt-mcp` package that lets you expose MCP tools to LLM clients.


## Watch the Video

I put together a walkthrough that covers the setup, and builds a simple project with the framework:

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fdegO5yNJw" title="Django Bolt Overview" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Why This Matters

If you are already invested in Django and you are hitting limits with request throughput, your options have been limited. You could switch to FastAPI and lose the Django ORM and Admin, or you could stick with Django and accept the performance ceiling. Django Bolt is the first thing I have seen that credibly offers Actix class throughput without leaving Django behind. It is still young and the docs are still filling in, but the architecture is sound and the trajectory is promising. Check out the [GitHub repository](https://github.com/dj-bolt/django-bolt) and the [official documentation](https://bolt.farhana.li/) if you want to give it a look.
