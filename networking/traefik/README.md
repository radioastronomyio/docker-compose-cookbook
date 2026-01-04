<!--
---
title: "Traefik Docker Setup"
description: "Docker Compose deployment for Traefik v3 cloud-native edge router"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: networking
  - tech: traefik
related_documents:
  - "[Networking README](../README.md)"
  - "[Official Docs](https://doc.traefik.io/traefik/)"
---
-->

# Traefik Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Traefik v3 is a cloud-native edge router that provides automatic service discovery, SSL termination via Let's Encrypt, and middleware configuration through Docker labels. It represents a "Configuration as Code" approach to reverse proxying.

---

## 1. Contents

```
traefik/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Domain name (for SSL certificates)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Create acme.json: `touch traefik_data/acme.json && chmod 600 traefik_data/acme.json`
3. Run `docker compose up -d`
4. Access dashboard at `http://localhost:8081`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| None required | - | Basic setup uses Docker labels |

### Docker Socket Integration

Traefik listens to the Docker socket. When a container starts with specific labels, Traefik automatically configures routing, SSL termination, and middleware. No restart required when adding services.

### Security Note

The dashboard (`api.insecure=true`) is exposed only for internal access on port 8081. In production facing the internet, secure the dashboard behind authentication middleware.

### Adding Services

Any container joining the `proxy` network with appropriate labels gets automatic routing:

```yaml
labels:
  - "traefik.enable=true"
  - "traefik.http.routers.myapp.rule=Host(`myapp.example.com`)"
```

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./traefik_data/acme.json` | Let's Encrypt certificates |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 80 | TCP | HTTP entrypoint |
| 443 | TCP | HTTPS entrypoint |
| 8081 | TCP | Dashboard |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://doc.traefik.io/traefik/) | Upstream docs |
| [Nginx Proxy Manager](../nginx-proxy-manager/README.md) | Alternative reverse proxy |
| [Networking](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
