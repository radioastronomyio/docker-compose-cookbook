<!--
---
title: "Bazarr Docker Setup"
description: "Docker Compose deployment for Bazarr subtitle automation"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: bazarr
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://wiki.bazarr.media/)"
---
-->

# Bazarr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Bazarr manages subtitle downloads for media files managed by Sonarr and Radarr. It is essential for accessibility and for users who consume foreign-language content. It scans your library, detects missing subtitles based on language profiles, and fetches them from providers like OpenSubtitles.

---

## 1. Contents

```
bazarr/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Sonarr and/or Radarr instances

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:6767`
4. Connect to Sonarr/Radarr and configure subtitle providers

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### File Permissions

Bazarr requires read/write access to the media library to save subtitle files (.srt, .ass) alongside video files. It must share the same PUID/PGID as Sonarr and Radarr to avoid permission conflicts when writing to the shared volume.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./bazarr_config` | Application configuration and database |
| `/mnt/storage` | Media library (needs write access for subtitles) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 6767 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Wiki](https://wiki.bazarr.media/) | Upstream docs |
| [Sonarr](../sonarr/README.md) | TV series automation |
| [Radarr](../radarr/README.md) | Movie automation |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
