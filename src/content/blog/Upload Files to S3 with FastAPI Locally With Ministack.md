---
title: "Upload Files to S3 with FastAPI, Locally with Ministack"
description: "Learn how to build a FastAPI application that uploads files to Amazon S3 — without an AWS account. Using Ministack, a free LocalStack alternative, you can run S3 entirely on your machine and test boto3-powered file uploads locally."
pubDate: "Aug 22 2026"
tags: ["python", "fastapi", "aws", "s3", "ministack", "boto3"]
heroImage: "/ministack.webp"
---

In this video, you'll learn how to upload files to Amazon S3 from a FastAPI application without ever touching the real AWS cloud. We use Ministack — a free, open-source LocalStack replacement that emulates AWS services on your machine — so you can develop and test your file upload workflow entirely locally.

<iframe width="560" height="315" src="https://www.youtube.com/embed/_RFUT8qqdAg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<!-- more -->

## What You'll Learn

By the end of this video, you will be able to:
- Upload files using FastAPI
- Run a local S3-compatible server with Ministack
- Create buckets and upload objects using `boto3`
- Build a file upload endpoint in FastAPI
- Point the AWS SDK at a custom endpoint URL for local development

## What is Ministack?

Ministack is a free, open-source AWS emulator — a lightweight LocalStack alternative. It emulates many AWS services (including S3) right on your machine, and it is drop-in compatible with `boto3`, the AWS CLI, Terraform, CDK, Pulumi, and any other AWS SDK or tool. This means the code you write against Ministack locally works unchanged when pointed at real AWS.

## Prerequisites

- Python 3.10+ installed
- Docker (for running Ministack)
- Basic familiarity with FastAPI

## Quick Start

Start Ministack with Docker:

```bash
docker run -p 4566:4566 ministackorg/ministack
```

Because Ministack speaks the same protocol as real S3, switching to production is as simple as removing the `endpoint_url` and adding your AWS credentials.

Watch the full video above for the complete step-by-step walkthrough.
