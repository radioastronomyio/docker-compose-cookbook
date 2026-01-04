<!--
---
title: "Scrutiny Docker Setup"
description: "Docker Compose deployment for Scrutiny hard drive health monitoring"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: scrutiny
related_documents:
  - "[Monitoring Logging README](../README.md)"
  - "[Official Docs](https://github.com/AnalogJ/scrutiny)"
---
-->

# Scrutiny Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Scrutiny provides a modern web dashboard for S.M.A.R.T. monitoring of hard drives. It tracks key metrics like temperature, reallocated sectors, power-on hours, and provides predictive failure analysis. Critical for protecting data on systems running intensive AI workloads.

---

## 1. Contents

```
scrutiny/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Root/privileged access for S.M.A.R.T. queries

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Update device paths in docker-compose.yml to match your drives
3. Run `docker compose up -d`
4. Access web UI at `http://localhost:8086`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| None required | - | Configuration via docker-compose devices |

### Hardware Access Requirements

Containerizing hardware monitoring requires special permissions. Scrutiny needs `cap_add: SYS_RAWIO` and `/run/udev` mapping to send raw SCSI/ATA commands to block devices. The "Omnibus" image bundles both the collector and web frontend.

### Device Mapping

Update the `devices` section to match your actual drives:

```yaml
devices:
  - /dev/sda
  - /dev/nvme0n1
```

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `scrutiny_config` | Application configuration |
| `scrutiny_influxdb` | Time-series metrics database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8086 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/AnalogJ/scrutiny) | Source code |
| [Netdata](../netdata/README.md) | System performance monitoring |
| [Monitoring Logging](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
