<!--
---
title: "Docmost Docker Setup"
description: "Docker Compose deployment for Docmost collaborative wiki"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: docmost
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://docmost.com/docs/)"
---
-->

# Docmost Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Docmost is a real-time collaborative documentation platform. It provides a Notion-like experience for team wikis and knowledge bases, with full self-hosting capability.

---

## 1. Contents

```
docmost/
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
3. Set `APP_SECRET` (min 32 chars) and `PG_PASSWORD`
4. Run `docker compose up -d`
5. Access UI at `http://localhost:3000`
6. Create workspace and admin account

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `DOCMOST_PORT` | 3000 | Web UI port |
| `APP_URL` | http://localhost:3000 | Public URL |
| `APP_SECRET` | - | Encryption key (min 32 chars) |
| `PG_PASSWORD` | - | PostgreSQL password |

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `docmost` | Node.js application |
| `db` | PostgreSQL for documents/users |
| `redis` | Real-time collaboration sync |

---

## 6. Real-Time Collaboration

Docmost uses WebSockets for live editing:

- Multiple users can edit simultaneously
- Changes sync instantly across clients
- Presence indicators show active editors

When using a reverse proxy, enable WebSocket support.

---

## 7. Features

| Feature | Description |
|---------|-------------|
| Block Editor | Notion-style content blocks |
| Workspaces | Organize content by team/project |
| Permissions | Role-based access control |
| Search | Full-text document search |
| Comments | Inline and page-level comments |
| Templates | Reusable page templates |
| API | REST API for integrations |

---

## 8. Data Persistence

| Volume | Purpose |
|--------|---------|
| `docmost_data` | Uploaded files, attachments |
| `db_data` | PostgreSQL database |
| `redis_data` | Session/collaboration cache |

---

## 9. Notion Comparison

| Aspect | Docmost | Notion |
|--------|---------|--------|
| Hosting | Self-hosted | Cloud |
| Data ownership | Full | Notion servers |
| Real-time collab | Yes | Yes |
| API | Yes | Yes |
| Databases | No | Yes |
| Cost | Free | Paid tiers |

Docmost focuses on documentation; Notion includes databases and more complex features.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docmost.com/docs/) | Upstream docs |
| [Web Application Servers](../README.md) | Parent category |
| [Authentik](../../security/authentik/README.md) | SSO integration |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
