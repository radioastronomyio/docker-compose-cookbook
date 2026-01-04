<!--
---
title: "Ghost Docker Setup"
description: "Docker Compose deployment for Ghost professional publishing platform"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: ghost
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://ghost.org/docs/)"
---
-->

# Ghost Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Ghost is a modern, headless CMS designed for professional publishing. It offers a clean writing experience and built-in SEO features, serving as a powerful alternative to WordPress for pure blogging and content-focused sites.

---

## 1. Contents

```
ghost/
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

1. Copy `.env.example` to `.env` and configure URLs/passwords
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:2368`
4. Navigate to `http://localhost:2368/ghost` for admin setup

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `GHOST_URL` | `http://localhost:2368` | Public site URL (critical) |
| `DB_PASS` | - | MySQL database password |
| `DB_ROOT_PASS` | - | MySQL root password |

### Critical: URL Configuration

The `url` environment variable is the most frequent failure point. If this does not strictly match the URL used to access the site (including https if using a reverse proxy), Ghost will trigger infinite redirect loops or fail to load assets.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `ghost_content` | Themes, images, and configuration |
| `ghost_db_data` | MySQL database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 2368 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://ghost.org/docs/) | Upstream docs |
| [Matomo](../../monitoring-logging/matomo/README.md) | Analytics |
| [Web Application Servers](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
