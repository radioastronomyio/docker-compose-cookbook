<!--
---
title: "Nginx Proxy Manager Docker Setup"
description: "Docker Compose deployment for Nginx Proxy Manager reverse proxy"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: networking
  - tech: nginx-proxy-manager
related_documents:
  - "[Networking README](../README.md)"
  - "[Official Docs](https://nginxproxymanager.com/)"
---
-->

# Nginx Proxy Manager Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Nginx Proxy Manager (NPM) provides a GUI for managing reverse proxy rules and SSL certificates. It consolidates ingress traffic for multiple services, handles Let's Encrypt automation, and eliminates the need to manually edit nginx configs.

---

## 1. Contents

```
nginx-proxy-manager/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ports 80, 443 available on host
- Domain name (for SSL certificates)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and set secure passwords
2. Run `docker compose up -d`
3. Access admin UI at `http://localhost:81`
4. Login with default credentials: `admin@example.com` / `changeme`
5. Change password immediately

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `NPM_HTTP_PORT` | 80 | HTTP ingress port |
| `NPM_HTTPS_PORT` | 443 | HTTPS ingress port |
| `NPM_ADMIN_PORT` | 81 | Admin UI port |
| `NPM_ROOT_PASS` | - | MariaDB root password |
| `NPM_DB_PASS` | - | MariaDB npm user password |

---

## 5. Shared Network Architecture

NPM creates a `proxy_net` network. Other services join this network to be proxied without exposing ports to the host:

```yaml
# In other service's docker-compose.yml
services:
  myapp:
    # No ports exposed to host
    networks:
      - proxy_net

networks:
  proxy_net:
    external: true
```

NPM then routes to `http://myapp:3000` internally.

---

## 6. SSL Certificates

NPM handles Let's Encrypt certificates automatically:

1. Add a Proxy Host in the UI
2. Enable SSL and select "Request a new SSL Certificate"
3. NPM handles challenge validation and renewal

Certificates renew automatically before expiration.

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `npm_data` | Proxy configurations, access lists |
| `npm_letsencrypt` | SSL certificates |
| `npm_mysql` | MariaDB database |

---

## 8. Common Proxy Configurations

| Service | Forward Hostname | Port | WebSocket |
|---------|-----------------|------|-----------|
| Nextcloud | nextcloud | 80 | No |
| Grafana | grafana | 3000 | Yes |
| Home Assistant | homeassistant | 8123 | Yes |
| Jellyfin | jellyfin | 8096 | Yes |

Enable WebSocket support for real-time applications.

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://nginxproxymanager.com/) | Upstream docs |
| [Networking](../README.md) | Parent category |
| [Authentik](../../security/authentik/README.md) | SSO integration |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
