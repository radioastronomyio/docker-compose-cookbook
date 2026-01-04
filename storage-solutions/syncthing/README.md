<!--
---
title: "Syncthing Docker Setup"
description: "Docker Compose deployment for Syncthing decentralized file synchronization"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: syncthing
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://docs.syncthing.net/)"
---
-->

# Syncthing Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Syncthing replaces proprietary cloud sync services (Dropbox, OneDrive, Google Drive) with an open, decentralized block exchange protocol. Files sync directly between your devices without passing through third-party servers.

---

## 1. Contents

```
syncthing/
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

1. Copy `.env.example` to `.env` and configure
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8384`
4. Add remote devices and configure shared folders

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### Port Requirements

Syncthing requires specific ports for peer discovery and data transfer:
- **22000/tcp+udp**: Data transfer between devices
- **21027/udp**: Local network discovery
- **8384/tcp**: Web UI

### Hostname Configuration

The `hostname` in docker-compose identifies this node to other devices in your mesh. Choose something descriptive like `docker-server` or `homelab-nas`.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./syncthing_config` | Device keys and configuration |
| `./syncthing_data` | Synchronized files |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8384 | TCP | Web UI |
| 22000 | TCP/UDP | Data transfer |
| 21027 | UDP | Local discovery |

---

## 7. Use Cases

- Sync Obsidian vaults across devices
- Backup camera rolls from mobile devices
- Sync KeePass databases securely
- Share project files between workstations

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.syncthing.net/) | Upstream docs |
| [Duplicati](../duplicati/README.md) | Backup solution |
| [Storage Solutions](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
