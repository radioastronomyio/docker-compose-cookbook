<!--
---
title: "Ntfy Docker Setup"
description: "Docker Compose deployment for Ntfy push notification server"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: messaging-collaboration
  - tech: ntfy
related_documents:
  - "[Messaging Collaboration README](../README.md)"
  - "[Official Docs](https://ntfy.sh/docs/)"
---
-->

# Ntfy Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Ntfy (pronounced "notify") allows you to send push notifications to your phone or desktop via simple HTTP PUT/POST requests. It acts as a unified alerting bus for scripts, backup jobs, monitoring tools, and automation workflows.

---

## 1. Contents

```
ntfy/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ntfy mobile app (iOS/Android) for receiving notifications

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8090`
4. Subscribe to a topic in the mobile app

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `NTFY_BASE_URL` | `http://localhost:8090` | Public server URL |
| `NTFY_AUTH_DEFAULT_ACCESS` | `deny-all` | Default access policy |

### Sending Notifications

```bash
# Simple notification
curl -d "Backup completed successfully" http://localhost:8090/mytopic

# With title and priority
curl -H "Title: Backup Status" -H "Priority: high" \
     -d "Backup completed" http://localhost:8090/mytopic
```

### Integration Examples

- Duplicati backup completion alerts
- Watchtower container update notifications
- Uptime Kuma status changes
- Cron job failure alerts

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./ntfy_cache` | Message cache for delivery reliability |
| `./ntfy_config` | Server configuration |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8090 | TCP | Web UI and API |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://ntfy.sh/docs/) | Upstream docs |
| [Uptime Kuma](../../monitoring-logging/uptime-kuma/README.md) | Status monitoring |
| [Messaging Collaboration](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
