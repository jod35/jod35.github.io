---
title: "msgspec - A Fast Pydantic Alternative That Supports YAML, TOML and MessagePack"
description: "msgspec is a fast and modern alternative to Pydantic for handling data validation and serialization in Python, supporting JSON, YAML, TOML, and MessagePack."
pubDate: "Jul 25 2026"
tags: ["python", "msgspec", "serialization", "performance"]
---

Msgspec is a fast and modern alternative to Pydantic for handling data validation and serialization in Python. It is built with performance in mind, making it a great choice when speed really matters, but it still keeps things simple and easy to use for developers.

One of the things that makes msgspec stand out is its support for multiple data formats like JSON, YAML, TOML, and MessagePack. This makes it flexible enough to fit into different kinds of projects, whether you are building APIs, working on data pipelines, or dealing with systems that process a lot of data quickly. <!-- more -->

## What Makes Msgspec Fast

Under the hood msgspec is written in C with zero required dependencies. The core of the library is the `Struct` base class, which is used to define efficient serializable objects. Compared to Python dataclasses or attrs, structs are 5 to 60 times faster for common operations like creation, comparison, encoding, and decoding. The JSON and MessagePack encoders and decoders regularly benchmark as the fastest options available for Python. In fact, msgspec can decode and validate JSON faster than orjson can decode it alone. For supported types, encoding or decoding a message with msgspec can be 10 to 80 times faster than alternative libraries.

## How It Works

You define your data structures by subclassing `msgspec.Struct` and adding type annotations. The types are not checked at runtime during normal use, which keeps things fast. Instead, validation happens when you decode incoming data using a typed decoder. This is where msgspec's approach differs from Pydantic, Pydantic checks types eagerly, while msgspec defers validation to decode time for maximum speed. Static type checkers like mypy and pyright work well with msgspec, so you catch bugs before your code ever runs.

```python
import msgspec

class User(msgspec.Struct):
    name: str
    age: int
    email: str

# Encoding
data = msgspec.json.encode(User(name="Alice", age=30, email="alice@example.com"))

# Decoding with validation
decoder = msgspec.json.Decoder(User)
user = decoder.decode(data)
print(user.name)  # "Alice"
```

Switching to a different format is as simple as changing the module you import from.

```python
# MessagePack (binary, faster than JSON)
data = msgspec.msgpack.encode(user)
user = msgspec.msgpack.Decoder(User).decode(data)

# YAML
data = msgspec.yaml.encode(user)
user = msgspec.yaml.Decoder(User).decode(data)

# TOML
data = msgspec.toml.encode(user)
user = msgspec.toml.Decoder(User).decode(data)
```

## How It Compares to Pydantic

Pydantic does more out of the box. It offers data coercion, complex validation logic, and deep integration with frameworks like FastAPI. If you need those features, Pydantic is the right choice. But if raw serialization speed is your priority and you do not need coercion, msgspec is significantly faster. It is also lighter, with no required dependencies and a fraction of the binary size. It is not a replacement for Pydantic in every scenario, but in the scenarios where it fits, the performance difference is hard to ignore.

## Ecosystem Adoption

Msgspec has been seeing increasing adoption across the Python ecosystem. It is used as the serialization layer in Litestar and Django Bolt, two frameworks I have written about recently. Several ASGI tools and message processing libraries have also adopted it. As more projects look to squeeze out every bit of performance, msgspec keeps showing up as the serialization backbone.

## Watch the Guide

Here is a walkthrough that covers how msgspec works, how it compares to Pydantic, and how you can use it in your projects:

<iframe width="560" height="315" src="https://www.youtube.com/embed/G8rMXsCAq6U" title="msgspec Overview" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

If you want to dig deeper, check out the [official documentation](https://msgspec.dev) and the [GitHub repository](https://github.com/msgspec/msgspec). It is one of those libraries that once you start using, you find yourself reaching for it more and more often.
