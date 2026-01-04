<!--
---
title: "Penpot Docker Setup"
description: "Docker Compose deployment for Penpot design platform"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: penpot
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://help.penpot.app/)"
---
-->

# Penpot Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Penpot is an open-source design and prototyping platform. It provides a browser-based Figma alternative using open standards (SVG), ensuring your designs remain portable and accessible.

---

## 1. Contents

```
penpot/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- 2GB+ RAM recommended

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secret: `openssl rand -base64 32`
3. Set `SECRET_KEY` and `PG_PASSWORD`
4. Temporarily set `PENPOT_FLAGS=enable-registration enable-login-with-password`
5. Run `docker compose up -d`
6. Access UI at `http://localhost:9001`
7. Create your account
8. Restore `PENPOT_FLAGS=disable-registration enable-login-with-password`
9. Restart: `docker compose up -d`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PENPOT_PORT` | 9001 | Web UI port |
| `PUBLIC_URI` | http://localhost:9001 | Public URL |
| `SECRET_KEY` | - | Encryption key (required) |
| `PG_PASSWORD` | - | PostgreSQL password |
| `PENPOT_FLAGS` | disable-registration... | Feature toggles |

### Feature Flags

Penpot uses a unique `PENPOT_FLAGS` variable for feature toggles:

| Flag | Description |
|------|-------------|
| `enable-registration` | Allow public signups |
| `disable-registration` | Private instance |
| `enable-login-with-password` | Password authentication |
| `enable-smtp` | Email notifications |
| `disable-email-verification` | Skip verification |

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `penpot-frontend` | Web UI (Nginx serving ClojureScript app) |
| `penpot-backend` | API and business logic |
| `penpot-exporter` | PDF/SVG export service |
| `penpot-postgres` | Design and user storage |
| `penpot-redis` | Session cache |

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Vector Design | Full vector editing tools |
| Prototyping | Interactive prototype creation |
| Components | Reusable design components |
| Design Systems | Shared styles and assets |
| Real-time Collab | Multiple editors simultaneously |
| SVG Export | Open standard format |
| Self-hosted Fonts | Custom font management |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `penpot_postgres` | Database (designs, users) |
| `penpot_assets` | Uploaded images, fonts, exports |

The assets volume can grow large with active use. Plan storage accordingly.

---

## 8. Figma Comparison

| Aspect | Penpot | Figma |
|--------|--------|-------|
| Hosting | Self-hosted | Cloud |
| Format | SVG (open) | Proprietary |
| Cost | Free | Free tier + paid |
| Plugins | Limited | Extensive |
| Performance | Good | Excellent |
| Offline | Yes (self-hosted) | Limited |

Penpot prioritizes open standards and data ownership over Figma's polish.

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://help.penpot.app/) | Upstream docs |
| [Web Application Servers](../README.md) | Parent category |
| [Authentik](../../security/authentik/README.md) | SSO integration |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
