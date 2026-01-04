<!--
---
title: "Authentik Docker Setup"
description: "Docker Compose deployment for Authentik identity provider"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: security
  - tech: authentik
related_documents:
  - "[Security README](../README.md)"
  - "[Official Docs](https://docs.goauthentik.io/)"
---
-->

# Authentik Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Authentik is an open-source Identity Provider (IdP) supporting SAML, OAuth2, OIDC, and LDAP. It provides Single Sign-On (SSO) across your self-hosted stack, replacing cloud services like Okta or Auth0.

---

## 1. Contents

```
authentik/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- 2GB+ RAM available

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secret key: `openssl rand -base64 32`
3. Set `AUTHENTIK_SECRET_KEY` and `PG_PASS`
4. Run `docker compose up -d`
5. Navigate to `http://localhost:9000/if/flow/initial-setup/`
6. Create your admin account

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `AUTHENTIK_PORT` | 9000 | HTTP web UI port |
| `AUTHENTIK_PORT_HTTPS` | 9443 | HTTPS web UI port |
| `PG_PASS` | - | PostgreSQL password (required) |
| `AUTHENTIK_SECRET_KEY` | - | Encryption key (required) |
| `AUTHENTIK_TAG` | 2024.10.0 | Authentik version |

### Secret Key Generation

The secret key encrypts sensitive data. Generate securely:

```bash
openssl rand -base64 32
```

**Never lose this key** — it's required to decrypt stored secrets.

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `server` | Web UI, API, authentication flows |
| `worker` | Background tasks, outpost management |
| `postgresql` | User data, configuration storage |
| `redis` | Session cache, task queue |

---

## 6. Supported Protocols

| Protocol | Use Case |
|----------|----------|
| OAuth2/OIDC | Modern web applications |
| SAML 2.0 | Enterprise applications |
| LDAP | Legacy system integration |
| Proxy | Header-based authentication |

---

## 7. Data Persistence

| Volume/Path | Purpose |
|-------------|---------|
| `database` | PostgreSQL data |
| `redis` | Session/cache data |
| `./media` | User uploads, branding |
| `./certs` | Custom certificates |

---

## 8. Outpost Deployment

Authentik uses "Outposts" to enforce authentication at the edge. The worker container can auto-discover containers via Docker socket and deploy outposts automatically.

For Nginx Proxy Manager integration:
1. Create a Proxy Provider in Authentik
2. Deploy a Proxy Outpost
3. Configure NPM to forward auth requests

---

## 9. Application Integration

Common integrations:

| Application | Protocol | Notes |
|-------------|----------|-------|
| Nextcloud | OIDC | Native support |
| Grafana | OAuth2 | Built-in OAuth |
| Portainer | OAuth2 | Business edition |
| Proxmox | OIDC | OpenID Connect realm |

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.goauthentik.io/) | Upstream docs |
| [Security](../README.md) | Parent category |
| [Vaultwarden](../vaultwarden/README.md) | Password management |
| [Nginx Proxy Manager](../../networking/nginx-proxy-manager/README.md) | Reverse proxy |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
