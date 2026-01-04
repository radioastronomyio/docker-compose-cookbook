<!--
---
title: "Dozzle Docker Setup"
description: "Docker Compose deployment for Dozzle real-time container log viewer"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: dozzle
related_documents:
  - "[Monitoring Logging README](../README.md)"
  - "[Official Docs](https://dozzle.dev/)"
---
-->

# Dozzle Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Dozzle provides a lightweight, web-based interface for viewing Docker container logs in real-time. It replaces the need to SSH into servers and run `docker logs -f` commands. Extremely efficient with a tiny memory footprint, streaming logs directly from the Docker API.

---

## 1. Contents

```
dozzle/
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
3. Access web UI at `http://localhost:8888`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `DOZZLE_NO_ANALYTICS` | true | Disable usage analytics |

### Features

- Real-time log streaming with minimal latency
- Regex filtering for complex log analysis
- Multi-container view
- Search across all logs
- Lightweight resource footprint

Particularly useful for debugging AI inference logs — tracking token generation speeds, OOM errors, or model loading issues.

---

## 5. Data Persistence

No persistence required. Dozzle streams logs directly from Docker without storing them.

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8888 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://dozzle.dev/) | Upstream docs |
| [Netdata](../netdata/README.md) | System performance monitoring |
| [Monitoring Logging](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
