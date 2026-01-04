<!--
---
title: "Jellyfin Docker Setup"
description: "Docker Compose deployment for Jellyfin media server with NVIDIA hardware transcoding"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: jellyfin
related_documents:
  - "[Media Entertainment README](../README.md)"
  - "[Official Docs](https://jellyfin.org/docs/)"
---
-->

# Jellyfin Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Jellyfin is the sovereign media streaming platform — a free, open-source alternative to Plex and Emby. It supports hardware-accelerated transcoding via NVIDIA NVENC/NVDEC, live TV, and extensive metadata management.

---

## 1. Contents

```
jellyfin/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU (optional, for hardware transcoding)
- NVIDIA Container Toolkit (if using GPU)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8096`
4. Complete initial setup wizard

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `JELLYFIN_URL` | `http://192.168.1.50:8096` | Public URL for discovery services |

### Hardware Transcoding Notes

- **NVIDIA_DRIVER_CAPABILITIES**: Set to `compute,video,utility` to enable NVENC/NVDEC while preserving CUDA for AI workloads
- The RTX 3080's dedicated encoding silicon can transcode simultaneously with AI inference
- A dedicated cache volume keeps transcoding segments off the metadata volume for better performance

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `jellyfin_config` | Server configuration and metadata |
| `jellyfin_cache` | Transcoding cache and temporary files |
| `/mnt/media` | Media library (bind mount) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8096 | TCP | HTTP Web UI |
| 8920 | TCP | HTTPS Web UI |
| 7359 | UDP | Auto-discovery |
| 1900 | UDP | DLNA |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://jellyfin.org/docs/) | Upstream docs |
| [Jellyseerr](../jellyseerr/README.md) | Request management frontend |
| [Sonarr](../sonarr/README.md) | TV series automation |
| [Radarr](../radarr/README.md) | Movie automation |
| [Media Entertainment](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
