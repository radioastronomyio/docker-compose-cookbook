<!--
---
title: "Jellyseerr Docker Setup"
description: "Docker Compose deployment for Jellyseerr media request management"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: jellyseerr
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://docs.seerr.dev/)"
---
-->

# Jellyseerr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Jellyseerr is a fork of Overseerr, specifically engineered to integrate with Jellyfin. It provides a polished, "Netflix-style" interface for users to discover content and request it. It acts as the user-facing frontend for the entire backend automation stack (Sonarr, Radarr).

---

## 1. Contents

```
jellyseerr/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Jellyfin instance
- Sonarr and/or Radarr instances

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:5055`
4. Connect to Jellyfin, Sonarr, and Radarr via their APIs

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `TZ` | America/New_York | Container timezone |
| `LOG_LEVEL` | debug | Logging verbosity (set to `info` for production) |

### Internal Service Communication

When all *Arr services run in the same Docker Compose stack (or shared network), Jellyseerr can communicate using container names (`http://sonarr:8989`) rather than IP addresses. This internal routing improves stability and security — inter-service traffic never leaves the Docker bridge network.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./jellyseerr_config` | Application configuration and database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 5055 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.seerr.dev/) | Upstream docs |
| [Jellyfin](../jellyfin/README.md) | Media streaming |
| [Sonarr](../sonarr/README.md) | TV series automation |
| [Radarr](../radarr/README.md) | Movie automation |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
