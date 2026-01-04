<!--
---
title: "Dockge Docker Setup"
description: "Docker Compose deployment for Dockge stack manager"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: container-management
  - tech: dockge
related_documents:
  - "[Container Management README](../README.md)"
  - "[GitHub Repository](https://github.com/louislam/dockge)"
---
-->

# Dockge Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Dockge is a compose-native stack manager from the creator of Uptime Kuma. While Portainer manages containers, Dockge manages compose stacks as code, providing a UI for editing docker-compose.yml files and managing environment variables.

---

## 1. Contents

```
dockge/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Dedicated stacks directory on host

---

## 3. Quick Start

1. Create stacks directory: `sudo mkdir -p /opt/stacks`
2. Copy `.env.example` to `.env`
3. Run `docker compose up -d`
4. Access UI at `http://localhost:5001`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `DOCKGE_PORT` | 5001 | Web UI port |
| `STACKS_DIR` | /opt/stacks | Host directory for compose stacks |

---

## 5. Key Features

| Feature | Description |
|---------|-------------|
| Reactive Terminal | Real-time streaming output for compose operations |
| YAML Editor | In-browser editing with syntax highlighting |
| Env Management | Edit .env files alongside compose files |
| One-Click Actions | Up, down, restart, pull with single click |
| Stack Versioning | Keep stack definitions safe on host filesystem |

---

## 6. Directory Structure

Dockge enforces a disciplined directory structure:

```
/opt/stacks/
├── my-app/
│   ├── docker-compose.yml
│   └── .env
├── another-app/
│   ├── docker-compose.yml
│   └── .env
└── ...
```

Each stack gets its own folder. This structure makes backup and version control trivial.

---

## 7. Data Persistence

| Path | Purpose |
|------|---------|
| `./dockge-data` | Dockge configuration and state |
| `${STACKS_DIR}` | All managed compose stacks (host-mounted) |

Even if the Dockge container is destroyed, your stack definitions remain safe on the host.

---

## 8. Portainer vs Dockge

| Aspect | Portainer | Dockge |
|--------|-----------|--------|
| Focus | Container management | Compose stack management |
| Complexity | Feature-rich | Minimalist |
| Storage | Database | Filesystem (YAML files) |
| Use Case | Daily container ops | Stack deployment/editing |

Many users run both: Portainer for container inspection, Dockge for stack management.

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/louislam/dockge) | Source code |
| [Container Management](../README.md) | Parent category |
| [Portainer](../portainer/README.md) | Container-focused alternative |
| [Uptime Kuma](../../monitoring-logging/uptime-kuma/README.md) | Same developer |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
