<!--
---
title: "Apache Guacamole Docker Setup"
description: "Docker Compose deployment for Apache Guacamole clientless remote desktop gateway"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: networking
  - tech: guacamole
related_documents:
  - "[Networking README](../README.md)"
  - "[Official Docs](https://guacamole.apache.org/doc/gug/)"
---
-->

# Apache Guacamole Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Apache Guacamole is a clientless remote desktop gateway supporting VNC, RDP, and SSH protocols. It provides secure, browser-based access to desktop environments or servers without requiring VPN clients — access any machine from any device with a web browser.

---

## 1. Contents

```
guacamole/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Initialize database schema (see Quick Start)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and set passwords
2. Initialize the database schema:
   ```bash
   docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --mysql > initdb.sql
   ```
3. Run `docker compose up -d`
4. Import schema: `docker exec -i guac_db mysql -u root -p guacamole_db < initdb.sql`
5. Access web UI at `http://localhost:8088/guacamole`
6. Default login: `guacadmin` / `guacadmin`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `MYSQL_PASSWORD` | - | Guacamole database user password |
| `DB_ROOT_PASS` | - | MySQL root password |

### Architecture

Guacamole is a 3-tier stack:
- **guacamole**: Web frontend (Java/Tomcat)
- **guacd**: Proxy daemon that performs protocol translation (RDP/VNC/SSH → HTML5)
- **guac_db**: MySQL database for users and connections

The `guacd` component handles the heavy lifting of protocol conversion.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `guac_db_data` | MySQL database (users, connections, history) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8088 | TCP | Web UI |

---

## 7. Adding Connections

After login, navigate to Settings → Connections to add:
- RDP connections to Windows machines
- VNC connections to Linux desktops
- SSH connections to servers

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://guacamole.apache.org/doc/gug/) | Upstream docs |
| [Code-Server](../../development-ci-cd/code-server/README.md) | Browser-based IDE |
| [Networking](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
