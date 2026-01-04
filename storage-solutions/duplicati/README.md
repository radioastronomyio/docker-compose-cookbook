<!--
---
title: "Duplicati Docker Setup"
description: "Docker Compose deployment for Duplicati backup and disaster recovery"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: duplicati
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://duplicati.readthedocs.io/)"
---
-->

# Duplicati Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Duplicati manages encrypted, incremental backups to local storage or cloud providers (S3, Backblaze B2, Google Drive, FTP, SSH). Its block-based deduplication saves significant storage space when backing up multiple versions of files.

---

## 1. Contents

```
duplicati/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Backup destination (local path, cloud storage, or remote server)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and configure
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8200`
4. Create a new backup job with wizard

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |

### Volume Mapping Strategy

- **Source data** (`/source`): Mount read-only (`:ro`) to prevent backup tool from accidentally modifying production data
- **Backup destination** (`/backups`): Local destination for backups (optional if using cloud)
- **Config** (`/config`): Duplicati database and job configurations

### Supported Destinations

- Local/Network: FTP, SSH/SFTP, WebDAV, SMB
- Cloud: Amazon S3, Backblaze B2, Google Drive, OneDrive, Dropbox
- Object Storage: Any S3-compatible storage

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./duplicati_config` | Job configurations and database |
| `/mnt/docker_volumes` | Source data to backup (read-only) |
| `./backups` | Local backup destination |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8200 | TCP | Web UI |

---

## 7. Backup Best Practices

- Use AES-256 encryption for all backups
- Store encryption passphrase securely (not in the backup)
- Test restore procedures regularly
- Use 3-2-1 backup rule: 3 copies, 2 media types, 1 offsite

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://duplicati.readthedocs.io/) | Upstream docs |
| [Syncthing](../syncthing/README.md) | File synchronization |
| [Ntfy](../../messaging-collaboration/ntfy/README.md) | Backup notifications |
| [Storage Solutions](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
