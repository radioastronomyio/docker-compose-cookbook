<!--
---
title: "Code-Server Docker Setup"
description: "Docker Compose deployment for Code-Server browser-based VS Code"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: development-ci-cd
  - tech: code-server
related_documents:
  - "[Development CI/CD README](../README.md)"
  - "[Official Docs](https://coder.com/docs/code-server/)"
---
-->

# Code-Server Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Code-server runs Visual Studio Code on a remote server, accessible via a web browser. It enables development on any device, including tablets, while leveraging the full power of your server's hardware (GPU access, fast compilation, large memory).

---

## 1. Contents

```
code-server/
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

1. Copy `.env.example` to `.env` and set password
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8443`
4. Enter password to access VS Code

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |
| `TZ` | America/New_York | Container timezone |
| `CODE_PASSWORD` | - | Access password |

### Development Environment Benefits

Running code-server on a powerful workstation (like an RTX 3080 system) provides:
- Direct GPU access for testing CUDA code
- Fast compilation using all available cores
- Large memory for resource-intensive tasks
- Consistent environment across devices

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./code_config` | VS Code settings and extensions |
| `/home/user/docker` | Project files (customize path) |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8443 | TCP | Web UI |

---

## 7. Security Considerations

- Always use a strong password
- Consider placing behind a reverse proxy with SSL
- Limit network access if possible
- The container runs as a non-root user (coder)

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://coder.com/docs/code-server/) | Upstream docs |
| [Guacamole](../../networking/guacamole/README.md) | Remote desktop access |
| [Development CI/CD](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
