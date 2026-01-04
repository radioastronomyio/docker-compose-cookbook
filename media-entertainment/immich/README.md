<!--
---
title: "Immich Docker Setup"
description: "Docker Compose deployment for Immich self-hosted photo management with ML"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: immich
related_documents:
  - "[Media & Entertainment README](../README.md)"
  - "[Official Docs](https://immich.app/docs/)"
---
-->

# Immich Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Immich is a self-hosted Google Photos alternative that uses AI for facial recognition and semantic search via CLIP embeddings, with full GPU acceleration support.

---

## 1. Contents

```
immich/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 4GB+ VRAM (for ML acceleration)
- NVIDIA Container Toolkit

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:2283`
4. Create admin account and start uploading

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `UPLOAD_LOCATION` | ./library | Photo storage path |
| `DB_PASSWORD` | postgres | Database password |
| `IMMICH_VERSION` | release | Version tag |

### GPU Acceleration

The `immich-machine-learning` container uses the `release-cuda` tag to leverage NVIDIA GPUs for:
- CLIP embeddings (semantic search)
- Facial recognition
- Object detection

This reduces indexing time from hours to minutes for large libraries.

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `immich-server` | Main application server |
| `immich-machine-learning` | GPU-accelerated ML processing |
| `redis` | Caching and job queue |
| `database` | PostgreSQL with pgvector |

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./library` | Photo and video storage |
| `model-cache` | ML model weights |
| `postgres_data` | Database |

---

## 7. Mobile Apps

Immich provides mobile apps for iOS and Android with automatic backup:
- [iOS App Store](https://apps.apple.com/app/immich/id1613945587)
- [Google Play Store](https://play.google.com/store/apps/details?id=app.alextran.immich)

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://immich.app/docs/) | Upstream docs |
| [Immich GitHub](https://github.com/immich-app/immich) | Source code |
| [Media & Entertainment](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
