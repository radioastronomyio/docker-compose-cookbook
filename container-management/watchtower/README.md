<!--
---
title: "Watchtower Docker Setup"
description: "Docker Compose deployment for Watchtower automated container updates"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: container-management
  - tech: watchtower
related_documents:
  - "[Container Management README](../README.md)"
  - "[Official Docs](https://containrrr.dev/watchtower/)"
---
-->

# Watchtower Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Watchtower automates the updating of Docker containers. It monitors the Docker socket, checks for new images on registries, and gracefully restarts containers with new images. Essential for maintaining security patches and feature updates across your container fleet.

---

## 1. Contents

```
watchtower/
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
3. Watchtower will check for updates every 24 hours

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `WATCHTOWER_POLL_INTERVAL` | 86400 | Check interval in seconds (default: 24h) |

### Update Strategy

The configuration uses conservative defaults:
- **24-hour polling interval**: Prevents aggressive API calls to Docker Hub
- **--cleanup flag**: Removes old images after updates (critical for large AI/ML images that can exceed 10GB)

### Production Considerations

Automatic updates can be risky. Consider:
- Using `--label-enable` to only update labeled containers
- Setting up notifications via `--notifications-url` (Discord, Slack, etc.)
- Testing in staging before production

---

## 5. Data Persistence

No persistence required. Watchtower is stateless.

---

## 6. Port Reference

No ports exposed. Watchtower operates via Docker socket only.

---

## 7. Selective Updates

To update only specific containers, add labels:

```yaml
# In target container
labels:
  - "com.centurylinklabs.watchtower.enable=true"
```

Then run Watchtower with `--label-enable` flag.

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://containrrr.dev/watchtower/) | Upstream docs |
| [Portainer](../portainer/README.md) | Container management UI |
| [Dockge](../dockge/README.md) | Compose stack manager |
| [Container Management](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
