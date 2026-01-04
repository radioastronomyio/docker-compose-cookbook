<!--
---
title: "Uptime Kuma Docker Setup"
description: "Docker Compose deployment for Uptime Kuma status monitoring"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: uptime-kuma
related_documents:
  - "[Monitoring & Logging README](../README.md)"
  - "[GitHub Repository](https://github.com/louislam/uptime-kuma)"
---
-->

# Uptime Kuma Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Uptime Kuma is a self-hosted monitoring tool for tracking HTTP/TCP/DNS/Docker endpoints. It provides a beautiful status dashboard and replaces paid services like UptimeRobot or PagerDuty for homelab and small business use.

---

## 1. Contents

```
uptime-kuma/
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
2. Run `docker compose up -d`
3. Access UI at `http://localhost:3001`
4. Create your admin account

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `UPTIME_KUMA_PORT` | 3001 | Web UI port |

---

## 5. Monitor Types

| Type | Description |
|------|-------------|
| HTTP(S) | Web endpoint monitoring with status codes |
| TCP | Port connectivity checks |
| DNS | DNS resolution monitoring |
| Docker | Container health status via socket |
| Ping | ICMP ping checks |
| Push | Heartbeat endpoints for cron jobs |
| Steam | Game server monitoring |
| MQTT | Message broker monitoring |

---

## 6. Docker Awareness

By mounting the Docker socket (read-only), Uptime Kuma can monitor container health status directly:

- Detects `unhealthy` state from failed healthchecks
- More accurate than port-based monitoring
- Shows container state transitions

To disable, remove the socket volume mount from docker-compose.yml.

---

## 7. Notifications

Supported notification channels:

- Email (SMTP)
- Discord, Slack, Telegram, Teams
- Pushover, Gotify, ntfy
- PagerDuty, Opsgenie
- Webhooks (custom integrations)
- 90+ total integrations

---

## 8. Data Persistence

| Volume | Purpose |
|--------|---------|
| `uptime-kuma-data` | SQLite database, configuration |

---

## 9. Status Pages

Create public status pages to share service health:

1. Settings → Status Pages → Add Status Page
2. Add monitors to the page
3. Share the public URL

Supports custom domains and branding.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/louislam/uptime-kuma) | Source code |
| [Monitoring & Logging](../README.md) | Parent category |
| [Dockge](../../container-management/dockge/README.md) | Same developer |
| [Beszel](../beszel/README.md) | System metrics complement |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
