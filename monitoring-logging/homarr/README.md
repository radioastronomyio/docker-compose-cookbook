<!--
---
title: "Homarr Docker Setup"
description: "Docker Compose deployment for Homarr dashboard"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: homarr
related_documents:
  - "[Monitoring & Logging README](../README.md)"
  - "[Official Docs](https://homarr.dev/docs)"
---
-->

# Homarr Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Homarr is a customizable dashboard that aggregates all your self-hosted services into a single "pane of glass." It provides quick access, status monitoring, and container management for your homelab.

---

## 1. Contents

```
homarr/
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
3. Access UI at `http://localhost:7575`
4. Configure authentication in Settings → Users

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `HOMARR_PORT` | 7575 | Web UI port |

---

## 5. Docker Integration

By mounting the Docker socket (read-only), Homarr provides:

- Container status indicators (up/down)
- One-click container restart
- Service auto-discovery

This makes Homarr a simplified Portainer alternative for daily use.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Customizable Layout | Drag-and-drop tile arrangement |
| Service Widgets | Weather, calendar, media stats |
| Docker Status | Live container health |
| Integrations | Sonarr, Radarr, Plex, and 50+ services |
| Custom Icons | Upload or use built-in icon library |
| Multiple Boards | Separate dashboards for different purposes |

---

## 7. Data Persistence

| Path | Purpose |
|------|---------|
| `./homarr/configs` | Dashboard configuration |
| `./homarr/icons` | Custom uploaded icons |
| `./homarr/data` | Application data |

---

## 8. Widget Integrations

Popular integrations:

| Service | Widget Type |
|---------|-------------|
| Sonarr/Radarr | Media calendar |
| Plex/Jellyfin | Now playing |
| qBittorrent | Download status |
| Pi-hole | DNS statistics |
| Proxmox | VM/CT status |

Configure API keys in each widget's settings.

---

## 9. Authentication

Homarr has no authentication by default. After first access:

1. Go to Settings → Users
2. Enable authentication
3. Create admin user
4. Optionally integrate with OIDC (Authentik)

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://homarr.dev/docs) | Upstream docs |
| [Monitoring & Logging](../README.md) | Parent category |
| [Uptime Kuma](../uptime-kuma/README.md) | Status monitoring |
| [Portainer](../../container-management/portainer/README.md) | Full container management |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
