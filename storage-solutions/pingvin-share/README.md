<!--
---
title: "Pingvin Share Docker Setup"
description: "Docker Compose deployment for Pingvin Share ephemeral file transfer"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: pingvin-share
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://stonith404.github.io/pingvin-share/)"
---
-->

# Pingvin Share Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Pingvin Share is a self-hosted alternative to WeTransfer. It solves the problem of sending large files (video renders, datasets, backups) to clients or colleagues without file size limits or third-party cloud tracking.

---

## 1. Contents

```
pingvin-share/
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

1. Copy `.env.example` to `.env` and set the public URL
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:3004`
4. Create an account to start sharing

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PINGVIN_URL` | `http://192.168.1.50:3004` | Public application URL |

### Key Features

- **Reverse Shares**: Allow external users to upload files to your server via secure, time-limited links
- **Expiring Links**: Set automatic expiration for shared files
- **Password Protection**: Secure shares with passwords
- **No File Size Limits**: Limited only by your storage

### Security Recommendation

Run behind a reverse proxy (Nginx Proxy Manager, Traefik) to provide SSL/TLS encryption, which is mandatory for secure file transfer over the internet.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./pingvin_data` | Database and file metadata |
| `./pingvin_images` | Preview images |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 3004 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://stonith404.github.io/pingvin-share/) | Upstream docs |
| [Syncthing](../syncthing/README.md) | Continuous file sync |
| [Storage Solutions](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
