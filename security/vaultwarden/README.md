<!--
---
title: "Vaultwarden Docker Setup"
description: "Docker Compose deployment for Vaultwarden password manager"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: security
  - tech: vaultwarden
related_documents:
  - "[Security README](../README.md)"
  - "[GitHub Repository](https://github.com/dani-garcia/vaultwarden)"
---
-->

# Vaultwarden Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Vaultwarden is a lightweight, Rust-based implementation of the Bitwarden API. It's fully compatible with official Bitwarden clients while requiring a fraction of the resources, making it ideal for self-hosting.

---

## 1. Contents

```
vaultwarden/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- HTTPS reverse proxy (for production)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access UI at `http://localhost:8085`
4. Create your account
5. Set `SIGNUPS_ALLOWED=false` in `.env`
6. Restart: `docker compose up -d`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `VAULTWARDEN_PORT` | 8085 | Web UI port |
| `SIGNUPS_ALLOWED` | true | Allow new registrations |
| `DOMAIN` | http://localhost:8085 | Public URL |
| `ADMIN_TOKEN` | - | Admin panel access token |

### Security Configuration

After creating your account(s):

```bash
# Edit .env
SIGNUPS_ALLOWED=false

# Restart
docker compose up -d
```

---

## 5. Client Setup

Use official Bitwarden clients with your Vaultwarden server:

1. Open Bitwarden app/extension
2. Click the gear icon (Settings)
3. Set "Server URL" to your Vaultwarden domain
4. Login with your credentials

Supported clients: Browser extensions, desktop apps, mobile apps, CLI.

---

## 6. WebSocket Sync

Real-time sync requires WebSocket support. When using a reverse proxy, ensure WebSocket upgrade is enabled:

For Nginx Proxy Manager:
- Enable "Websockets Support" on the proxy host

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `vw-data` | Vault database, attachments, icons |

**Critical**: Back up this volume regularly. It contains your encrypted vault.

---

## 8. Admin Panel

Enable the admin panel for user management:

```bash
# Generate token
openssl rand -base64 48

# Add to .env
ADMIN_TOKEN=<generated-token>
```

Access at `http://localhost:8085/admin`

---

## 9. Production Checklist

- [ ] HTTPS via reverse proxy
- [ ] `SIGNUPS_ALLOWED=false`
- [ ] Strong master passwords
- [ ] 2FA enabled for all users
- [ ] Regular backups of `/data`
- [ ] Firewall rules limiting access

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/dani-garcia/vaultwarden) | Source code |
| [Bitwarden Clients](https://bitwarden.com/download/) | Official clients |
| [Security](../README.md) | Parent category |
| [Authentik](../authentik/README.md) | SSO integration |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
