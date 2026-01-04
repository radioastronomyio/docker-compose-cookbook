<!--
---
title: "Listmonk Docker Setup"
description: "Docker Compose deployment for Listmonk newsletter and mailing list manager"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: messaging-collaboration
  - tech: listmonk
related_documents:
  - "[Messaging Collaboration README](../README.md)"
  - "[Official Docs](https://listmonk.app/docs/)"
---
-->

# Listmonk Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Listmonk is a high-performance, self-hosted newsletter and mailing list manager. Written in Go as a single binary, it is incredibly resource-efficient compared to PHP-based alternatives like Mailchimp or TinyLetter.

---

## 1. Contents

```
listmonk/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- SMTP server for sending emails

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and set database password
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:9000`
4. Default login: `listmonk` / `listmonk`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `DB_PASS` | - | PostgreSQL database password |

### Auto-Installation

The command includes `--install --idempotent` which automatically sets up the database schema on first run and safely handles upgrades on subsequent starts.

### SMTP Configuration

Configure SMTP settings in the admin UI after first login:
- Settings → SMTP → Add new SMTP server
- Test connection before sending campaigns

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `listmonk_db_data` | PostgreSQL database (subscribers, campaigns, templates) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 9000 | TCP | Web UI |

---

## 7. Features

- High-performance bulk email sending
- Template management with WYSIWYG editor
- Subscriber segmentation and tagging
- Campaign analytics and tracking
- Import/export functionality
- REST API for automation

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://listmonk.app/docs/) | Upstream docs |
| [Ghost](../../web-application-servers/ghost/README.md) | Blog platform |
| [Messaging Collaboration](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
