<!--
---
title: "Radarr Docker Setup"
description: "Docker Compose deployment for Radarr movie lifecycle management"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: radarr
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://wiki.servarr.com/radarr)"
---
-->

# Radarr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Radarr performs the same function as Sonarr but is specialized for feature films. It handles complex naming conventions, release windows, and quality profiles specific to movies. It integrates with Prowlarr for indexers and sends downloads to your preferred client.

---

## 1. Contents

```
radarr/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Download client (qBittorrent, SABnzbd, etc.)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:7878`
4. Configure download client and root folders

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### Resource Usage Pattern

Radarr's resource usage is "bursty" — it idles with low consumption but spikes during library imports or upgrade scans. Leave CPU limits unbounded on shared hosts. Like Sonarr, the unified volume strategy is non-negotiable for I/O performance.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./radarr_config` | Application configuration and database |
| `/mnt/storage` | Unified mount for downloads and media (enables atomic moves) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 7878 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Wiki](https://wiki.servarr.com/radarr) | Upstream docs |
| [Prowlarr](../prowlarr/README.md) | Indexer management |
| [Sonarr](../sonarr/README.md) | TV series automation |
| [Jellyfin](../jellyfin/README.md) | Media streaming |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
