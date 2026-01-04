<!--
---
title: "Baserow Docker Setup"
description: "Docker Compose deployment for Baserow open-source no-code database"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: baserow
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://baserow.io/docs/)"
---
-->

# Baserow Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Baserow is a scalable, open-source alternative to Airtable. It enables the creation of complex relational databases with a user-friendly spreadsheet interface, supporting APIs for integration with automation tools like n8n.

---

## 1. Contents

```
baserow/
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

1. Copy `.env.example` to `.env` and set the public URL
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:3001`
4. Create an account to get started

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `BASEROW_PUBLIC_URL` | `http://192.168.1.50:3001` | Public URL (critical for CORS) |

### Critical: BASEROW_PUBLIC_URL

This is the single most important setting. It controls CORS headers and internal API routing. If you place Baserow behind a reverse proxy, this must be set to the final HTTPS URL, or the frontend will fail to communicate with the backend.

### All-in-One Architecture

The All-in-One image bundles:
- Backend (Django)
- Frontend (Nuxt.js)
- Database (PostgreSQL)
- Cache (Redis)

These are orchestrated internally via supervisord for simplified deployment.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `baserow_data` | All application data, database, and uploads |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 3001 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://baserow.io/docs/) | Upstream docs |
| [n8n](../../automation-orchestration/n8n/README.md) | Workflow automation |
| [Web Application Servers](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
