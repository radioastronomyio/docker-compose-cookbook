<!--
---
title: "Portainer Docker Setup"
description: "Docker Compose deployment for Portainer container management"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: container-management
  - tech: portainer
related_documents:
  - "[Container Management README](../README.md)"
  - "[Official Docs](https://docs.portainer.io/)"
---
-->

# Portainer Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Portainer is the de facto standard GUI for Docker management, providing visibility into containers, images, volumes, and networks. It replaces command-line Docker operations with a web interface for day-to-day administration.

---

## 1. Contents

```
portainer/
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

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access UI at `https://localhost:9443`
4. Create your admin account (first user becomes admin)

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PORTAINER_PORT` | 9443 | HTTPS web UI port |
| `PORTAINER_HTTP_PORT` | 9000 | HTTP web UI port (optional) |

---

## 5. Security Considerations

Portainer requires Docker socket access to function, granting it root-equivalent privileges on the host.

**Best practices:**

- Use HTTPS (port 9443) exclusively
- Set a strong admin password immediately
- Consider Docker socket proxy for isolation
- Never expose directly to the internet without VPN/firewall

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Container Management | Start, stop, restart, logs, exec |
| Image Management | Pull, build, remove images |
| Volume Management | Create, inspect, remove volumes |
| Network Management | Create and manage Docker networks |
| Stack Deployment | Deploy compose stacks via UI |
| Resource Monitoring | CPU, memory, network stats |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `portainer_data` | User accounts, settings, encryption keys |

---

## 8. Standalone vs Edge Agent

This recipe deploys Portainer standalone for single-node management. For multi-node clusters, consider:

- **Edge Agent**: Secure tunnel for remote nodes
- **Portainer Business**: Advanced features for enterprise

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.portainer.io/) | Upstream docs |
| [Container Management](../README.md) | Parent category |
| [Dockge](../dockge/README.md) | Compose-focused alternative |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
