<!--
---
title: "Matomo Docker Setup"
description: "Docker Compose deployment for Matomo web analytics platform"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: matomo
related_documents:
  - "[Monitoring Logging README](../README.md)"
  - "[Official Docs](https://matomo.org/docs/)"
---
-->

# Matomo Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Matomo is a comprehensive web analytics platform that provides 100% data ownership and GDPR compliance. It serves as a direct alternative to Google Analytics, giving you insight into user interactions with your self-hosted services without feeding data to third-party ad networks.

---

## 1. Contents

```
matomo/
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

1. Copy `.env.example` to `.env` and set database password
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8093`
4. Complete installation wizard

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `DB_PASS` | - | MariaDB database password |

### Use Cases

Track user interactions with your self-hosted services:
- Blog traffic (Ghost)
- Documentation usage (BookStack)
- Application analytics (Invoice Ninja)

All data stays on your infrastructure — no third-party tracking.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `matomo_html` | Application files and configuration |
| `matomo_db_data` | MariaDB database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8093 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://matomo.org/docs/) | Upstream docs |
| [Ghost](../../web-application-servers/ghost/README.md) | Blog platform |
| [Monitoring Logging](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
