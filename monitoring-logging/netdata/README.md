<!--
---
title: "Netdata Docker Setup"
description: "Docker Compose deployment for Netdata real-time performance monitoring"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: netdata
related_documents:
  - "[Monitoring Logging README](../README.md)"
  - "[Official Docs](https://learn.netdata.cloud/)"
---
-->

# Netdata Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Netdata offers high-resolution, real-time performance monitoring. Unlike standard dashboarding tools that poll every minute, Netdata updates every second, providing immediate visibility into system spikes. It automatically detects NVIDIA GPUs and provides detailed VRAM, PCIe, and compute metrics.

---

## 1. Contents

```
netdata/
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
3. Access web UI at `http://localhost:19999`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `NETDATA_CLAIM_TOKEN` | - | Optional: Connect to Netdata Cloud |

### Privileged Access

Netdata requires extensive host access for deep observability:
- `network_mode: host` — monitors host network interfaces directly
- `pid: host` — bypasses Docker's PID isolation
- Mounts `/proc`, `/sys`, and Docker socket read-only

This configuration is necessary for comprehensive system monitoring but should be understood before deployment.

### GPU Monitoring

Netdata automatically detects NVIDIA GPUs and provides detailed charts on VRAM usage, PCIe bandwidth, and compute load — invaluable for visualizing AI workload impact.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `netdataconfig` | Configuration files |
| `netdatalib` | Application data |
| `netdatacache` | Metrics cache |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 19999 | TCP | Web UI (host network mode) |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://learn.netdata.cloud/) | Upstream docs |
| [Scrutiny](../scrutiny/README.md) | Drive health monitoring |
| [Monitoring Logging](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
