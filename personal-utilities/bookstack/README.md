<!--
---
title: "BookStack Docker Setup"
description: "Docker Compose deployment for BookStack documentation platform"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: bookstack
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://www.bookstackapp.com/docs/)"
---
-->

# BookStack Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

BookStack is an opinionated wiki system that organizes information into a hierarchy of Books, Chapters, and Pages. It is ideal for documenting home lab infrastructure, technical procedures, and knowledge bases with a clean, intuitive interface.

---

## 1. Contents

```
bookstack/
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

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:6875`
4. Default login: `admin@admin.com` / `password`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `BOOKSTACK_URL` | `http://192.168.1.50:6875` | Public URL (critical for assets) |
| `BOOKSTACK_DB_PASS` | - | Database password |
| `DB_ROOT_PASS` | - | MariaDB root password |

### Critical: APP_URL Configuration

BookStack is strict about URL generation. If `BOOKSTACK_URL` does not match the exact URL used to access the site (including http vs https), images will fail to load and redirects will break. Always verify this matches your access URL.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `bookstack_config` | Application configuration and uploads |
| `bookstack_db_data` | MariaDB database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 6875 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://www.bookstackapp.com/docs/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
