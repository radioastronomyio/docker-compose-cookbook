<!--
---
title: "Postiz Docker Setup"
description: "Docker Compose deployment for Postiz social media automation"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: automation-orchestration
  - tech: postiz
related_documents:
  - "[Automation & Orchestration README](../README.md)"
  - "[Official Site](https://postiz.com/)"
---
-->

# Postiz Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Postiz is an open-source social media scheduling and automation platform. It allows you to schedule posts, manage multiple accounts, and automate content distribution across platforms like X (Twitter), LinkedIn, and more.

---

## 1. Contents

```
postiz/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- OAuth credentials for target platforms

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secret: `openssl rand -base64 32`
3. Set `JWT_SECRET` and `PG_PASSWORD`
4. Run `docker compose up -d`
5. Access UI at `http://localhost:5000`
6. Create account and connect social platforms

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `POSTIZ_PORT` | 5000 | Web UI port |
| `FRONTEND_URL` | http://localhost:5000 | Public URL |
| `JWT_SECRET` | - | Authentication key (required) |
| `PG_PASSWORD` | - | PostgreSQL password |

---

## 5. Supported Platforms

| Platform | Features |
|----------|----------|
| X (Twitter) | Posts, threads, scheduling |
| LinkedIn | Posts, articles |
| Facebook | Pages, groups |
| Instagram | Posts (via Meta API) |
| TikTok | Video posts |
| Pinterest | Pins |

Platform availability depends on API access and OAuth configuration.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Scheduling | Queue posts for future publication |
| Multi-account | Manage multiple social accounts |
| Calendar View | Visual content calendar |
| Analytics | Basic engagement metrics |
| Team Collaboration | Multiple users per workspace |
| AI Assistance | Content suggestions (optional) |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `db-data` | PostgreSQL (accounts, posts, schedules) |

---

## 8. Platform Authentication

Each platform requires OAuth credentials:

1. Register your app with the platform's developer portal
2. Obtain client ID and secret
3. Configure callback URL: `{FRONTEND_URL}/api/auth/callback/{platform}`
4. Add credentials in Postiz settings

---

## 9. Buffer/Hootsuite Comparison

| Aspect | Postiz | Buffer/Hootsuite |
|--------|--------|------------------|
| Hosting | Self-hosted | Cloud |
| Cost | Free | $5-100+/mo |
| Data ownership | Full | Third-party |
| Platforms | Growing | Comprehensive |
| Analytics | Basic | Advanced |

Postiz is ideal for teams wanting scheduling basics with full data control.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Postiz Website](https://postiz.com/) | Project site |
| [Automation & Orchestration](../README.md) | Parent category |
| [n8n](../n8n/README.md) | Advanced workflow automation |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
