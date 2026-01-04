<!--
---
title: "Linkwarden Docker Setup"
description: "Docker Compose deployment for Linkwarden collaborative bookmark manager"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: linkwarden
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://docs.linkwarden.app/)"
---
-->

# Linkwarden Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Linkwarden goes beyond simple bookmarking — it creates a self-hosted "Wayback Machine." For every link saved, it captures a screenshot and a PDF, ensuring that content remains accessible even if the original site goes offline (Link Rot protection).

---

## 1. Contents

```
linkwarden/
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
2. Generate NEXTAUTH_SECRET: `openssl rand -hex 32`
3. Run `docker compose up -d`
4. Access web UI at `http://localhost:3002`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `POSTGRES_PASSWORD` | - | PostgreSQL database password |
| `NEXTAUTH_URL` | `http://localhost:3002` | Public URL for authentication |
| `NEXTAUTH_SECRET` | - | Session encryption key (generate with openssl) |

### Resource Considerations

Linkwarden uses Playwright for headless browsing to capture screenshots. This process can be memory-intensive during bulk imports. Monitor container memory if deploying on constrained hardware.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `linkwarden_data` | Screenshots, PDFs, and application data |
| `linkwarden_pgdata` | PostgreSQL database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 3002 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.linkwarden.app/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
