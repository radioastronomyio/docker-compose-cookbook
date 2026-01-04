<!--
---
title: "Prowlarr Docker Setup"
description: "Docker Compose deployment for Prowlarr indexer manager"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: prowlarr
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://wiki.servarr.com/prowlarr)"
---
-->

# Prowlarr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Prowlarr is a modern indexer manager that integrates seamlessly with the *Arr stack (Sonarr, Radarr, Lidarr, Readarr). It replaces legacy Jackett by managing API keys and synchronization for Torrent trackers and Usenet indexers as a single source of truth.

---

## 1. Contents

```
prowlarr/
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
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:9696`
4. Configure indexers and sync to downstream *Arr apps

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### Sync Capability

Prowlarr's key feature is "sync" — configure indexers once in Prowlarr, then it pushes configurations to Sonarr, Radarr, and other *Arr apps via API. This eliminates redundant configuration and ensures consistency.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./prowlarr_config` | Application configuration and database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 9696 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Wiki](https://wiki.servarr.com/prowlarr) | Upstream docs |
| [Sonarr](../sonarr/README.md) | TV series automation |
| [Radarr](../radarr/README.md) | Movie automation |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
