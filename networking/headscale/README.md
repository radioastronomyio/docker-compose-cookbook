<!--
---
title: "Headscale Docker Setup"
description: "Docker Compose deployment for Headscale self-hosted Tailscale control server"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: networking
  - tech: headscale
related_documents:
  - "[Networking README](../README.md)"
  - "[Official Docs](https://headscale.net/)"
---
-->

# Headscale Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Headscale is an open-source, self-hosted implementation of the Tailscale control server. It enables a private WireGuard-based mesh network connecting all your devices (phones, laptops, servers) as if on the same LAN, without relying on Tailscale's proprietary coordination servers.

---

## 1. Contents

```
headscale/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- config.yaml (download from Headscale repository)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Download config.yaml: `curl -o headscale_config/config.yaml https://raw.githubusercontent.com/juanfont/headscale/main/config-example.yaml`
3. Edit config.yaml with your server URL and settings
4. Run `docker compose up -d`
5. Create a user: `docker exec headscale headscale users create myuser`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| None required | - | Configuration via config.yaml |

### Architecture

Headscale manages public key exchange and node coordination — it is strictly a control plane. Data traffic travels peer-to-peer between devices via NAT traversal techniques. Your actual traffic never touches the Headscale server.

### ROI

- Unlimited users and devices (vs Tailscale's free tier limits)
- Complete privacy of your network topology
- No dependency on third-party coordination servers

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./headscale_config` | Configuration and database |
| `./headscale_data` | Runtime data |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8085 | TCP | Control plane API |
| 9090 | TCP | Metrics |

---

## 7. Client Setup

Install Tailscale client on devices, then connect to your Headscale server:

```bash
tailscale up --login-server https://headscale.yourdomain.com
```

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://headscale.net/) | Upstream docs |
| [WireGuard](../wireguard/README.md) | Alternative VPN |
| [Networking](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
