<!--
---
title: "GlitchTip Docker Setup"
description: "Docker Compose deployment for GlitchTip error tracking"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: glitchtip
related_documents:
  - "[Monitoring & Logging README](../README.md)"
  - "[Official Docs](https://glitchtip.com/documentation)"
---
-->

# GlitchTip Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

GlitchTip is an open-source, Sentry-compatible error tracking platform. It captures exceptions from your applications, providing stack traces, context, and trends to help debug production issues.

---

## 1. Contents

```
glitchtip/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secret: `openssl rand -base64 32`
3. Set `GLITCHTIP_SECRET` and `PG_PASSWORD`
4. Run `docker compose up -d`
5. Create superuser (see below)
6. Access UI at `http://localhost:8000`

### Create Superuser

```bash
docker exec -it glitchtip-web ./manage.py createsuperuser
```

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `GLITCHTIP_PORT` | 8000 | Web UI port |
| `PG_PASSWORD` | - | PostgreSQL password (required) |
| `GLITCHTIP_SECRET` | - | Django secret key (required) |
| `GLITCHTIP_DOMAIN` | http://localhost:8000 | Public URL |
| `EMAIL_URL` | consolemail:// | SMTP configuration |

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `web` | Django web application |
| `worker` | Celery background tasks |
| `postgres` | Event and project storage |
| `redis` | Task queue broker |

---

## 6. SDK Integration

GlitchTip is Sentry-compatible. Use official Sentry SDKs with your GlitchTip DSN:

```python
# Python example
import sentry_sdk

sentry_sdk.init(
    dsn="http://key@localhost:8000/1",
    traces_sample_rate=1.0,
)
```

Supported languages: Python, JavaScript, Go, Ruby, PHP, Java, .NET, and more.

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `pg-data` | PostgreSQL database |
| `uploads` | Source maps, attachments |

---

## 8. Features

| Feature | Description |
|---------|-------------|
| Error Grouping | Automatic deduplication of similar errors |
| Stack Traces | Full context with local variables |
| Release Tracking | Associate errors with deployments |
| Source Maps | JavaScript error translation |
| Uptime Monitoring | Basic HTTP endpoint checks |
| Performance | Transaction tracing (limited) |

---

## 9. GlitchTip vs Sentry

| Aspect | GlitchTip | Sentry |
|--------|-----------|--------|
| License | Open source | Open core |
| Resources | ~500MB RAM | ~2GB+ RAM |
| Features | Core error tracking | Full APM suite |
| Self-host | Simple | Complex |

GlitchTip is ideal for smaller teams needing essential error tracking without Sentry's resource footprint.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://glitchtip.com/documentation) | Upstream docs |
| [Sentry SDKs](https://docs.sentry.io/platforms/) | Compatible client libraries |
| [Monitoring & Logging](../README.md) | Parent category |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
