<!--
---
title: "Twenty Docker Setup"
description: "Docker Compose deployment for Twenty open source CRM"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: twenty
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://docs.twenty.com/)"
---
-->

# Twenty Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Twenty is an open-source CRM that provides a modern alternative to Salesforce and HubSpot. It offers contact management, deal pipelines, and activity tracking with full data sovereignty.

---

## 1. Contents

```
twenty/
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
3. Set `APP_SECRET`, `PG_PASSWORD`, and `SERVER_URL`
4. Run `docker compose up -d`
5. Access UI at `http://localhost:3000`
6. Create workspace and admin account

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `TWENTY_PORT` | 3000 | Web UI port |
| `SERVER_URL` | http://localhost:3000 | Public URL (critical for auth) |
| `APP_SECRET` | - | Encryption key (required) |
| `PG_PASSWORD` | - | PostgreSQL password |

### SERVER_URL

The `SERVER_URL` must match your actual access URL. Incorrect configuration breaks:
- OAuth callbacks
- Email links
- API integrations

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `server` | API and web frontend |
| `worker` | Background job processing |
| `db` | PostgreSQL for CRM data |
| `redis` | Job queue and caching |

---

## 6. Features

| Feature | Description |
|---------|-------------|
| People | Contact management with custom fields |
| Companies | Organization tracking |
| Opportunities | Deal pipeline with stages |
| Activities | Tasks, notes, emails, calls |
| Views | Custom filtered views |
| API | GraphQL API for integrations |
| Import/Export | CSV data migration |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `server-local-data` | File uploads, attachments |
| `db-data` | PostgreSQL database |

---

## 8. Salesforce Comparison

| Aspect | Twenty | Salesforce |
|--------|--------|------------|
| Hosting | Self-hosted | Cloud |
| Cost | Free | $25-300/user/mo |
| Customization | Open source | Configuration |
| Data ownership | Full | Salesforce servers |
| Complexity | Simple | Enterprise |

Twenty targets small-to-medium teams wanting CRM essentials without enterprise complexity.

---

## 9. Integrations

Twenty supports integrations via:

- **GraphQL API**: Full data access
- **Webhooks**: Event-driven automation
- **Zapier/n8n**: Workflow connections

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.twenty.com/) | Upstream docs |
| [Web Application Servers](../README.md) | Parent category |
| [n8n](../../automation-orchestration/n8n/README.md) | Workflow automation |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
