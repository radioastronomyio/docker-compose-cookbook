<!--
---
title: "Nextcloud AIO Docker Setup"
description: "Docker Compose deployment for Nextcloud All-in-One"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: nextcloud
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://github.com/nextcloud/all-in-one)"
---
-->

# Nextcloud AIO Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Nextcloud All-in-One (AIO) is the official, turnkey deployment method for Nextcloud. It replaces Dropbox, Google Drive, and Google Photos with a self-hosted solution featuring file sync, calendar, contacts, and office collaboration.

---

## 1. Contents

```
nextcloud-aio/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Domain name (for SSL in production)
- Ports 80, 443, 8080 available

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access `https://localhost:8080` (accept self-signed cert)
4. Copy the initial password displayed
5. Follow the setup wizard

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `AIO_PORT` | 8080 | AIO dashboard port |
| `APACHE_PORT` | 11000 | Nextcloud web port (for reverse proxy) |
| `UPLOAD_LIMIT` | 10G | Maximum file upload size |
| `MEMORY_LIMIT` | 1024M | PHP memory limit |
| `TZ` | America/New_York | Timezone |

---

## 5. Mastercontainer Architecture

Unlike traditional Nextcloud deployments, AIO uses a privileged orchestrator:

1. **Mastercontainer**: Spawns and manages sibling containers
2. **Automatic updates**: Containers updated via dashboard
3. **Built-in backup**: BorgBackup with encryption
4. **Optional services**: Collabora, Talk, Imaginary enabled via UI

The mastercontainer communicates with Docker via the socket to manage the full stack.

---

## 6. Managed Containers

AIO automatically deploys:

| Container | Purpose |
|-----------|---------|
| nextcloud-aio-apache | Web server |
| nextcloud-aio-database | PostgreSQL |
| nextcloud-aio-redis | Session cache |
| nextcloud-aio-nextcloud | PHP application |
| nextcloud-aio-notify-push | Real-time sync (Rust) |
| nextcloud-aio-borgbackup | Encrypted backups |

Optional: Collabora, Talk, Imaginary, ClamAV, Fulltextsearch.

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `nextcloud_aio_mastercontainer` | Orchestration state, backup keys |

**Critical**: This volume contains backup encryption keys. Never delete without extracting keys first.

Additional volumes are created automatically by AIO for data, database, etc.

---

## 8. Reverse Proxy Setup

For production with existing reverse proxy:

1. Set `APACHE_PORT=11000` and `APACHE_IP_BINDING=127.0.0.1`
2. Configure reverse proxy to forward to `localhost:11000`
3. Enter your domain in the AIO wizard
4. Enable HSTS and proper headers

See [AIO reverse proxy docs](https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md).

---

## 9. High Performance Backend

AIO includes Notify Push, a Rust-based service for instant file sync:

- WebSocket connections for real-time updates
- Eliminates client polling
- Significantly reduces server load

Enabled by default in AIO.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [AIO GitHub](https://github.com/nextcloud/all-in-one) | Source and docs |
| [Nextcloud Documentation](https://docs.nextcloud.com/) | Full Nextcloud docs |
| [Storage Solutions](../README.md) | Parent category |
| [Nginx Proxy Manager](../../networking/nginx-proxy-manager/README.md) | Reverse proxy |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
