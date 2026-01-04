<!--
---
title: "Sonarr Docker Setup"
description: "Docker Compose deployment for Sonarr TV series lifecycle management"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: sonarr
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://wiki.servarr.com/sonarr)"
---
-->

# Sonarr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Sonarr automates the tracking, retrieval, and organization of television series. It monitors RSS feeds for new episodes, interfaces with Prowlarr for indexers, sends download instructions to clients (qBittorrent, SABnzbd), and renames/moves finished files to the library.

---

## 1. Contents

```
sonarr/
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
3. Access web UI at `http://localhost:8989`
4. Configure download client and root folders

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### Atomic Moves Strategy

The most critical deployment consideration is volume mapping. To enable Atomic Moves (instant file imports via hardlinks), the download client and Sonarr must see an identical filesystem structure. Mount a unified parent directory `/data` containing both `/data/downloads` and `/data/tv`. This prevents slow copy-and-delete operations and saves disk space.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./sonarr_config` | Application configuration and database |
| `/mnt/storage` | Unified mount for downloads and media (enables atomic moves) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8989 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Wiki](https://wiki.servarr.com/sonarr) | Upstream docs |
| [Prowlarr](../prowlarr/README.md) | Indexer management |
| [Radarr](../radarr/README.md) | Movie automation |
| [Jellyfin](../jellyfin/README.md) | Media streaming |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
