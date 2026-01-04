<!--
---
title: "Beszel Docker Setup"
description: "Docker Compose deployment for Beszel lightweight metrics hub"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: monitoring-logging
  - tech: beszel
related_documents:
  - "[Monitoring & Logging README](../README.md)"
  - "[GitHub Repository](https://github.com/henrygd/beszel)"
---
-->

# Beszel Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Beszel is a lightweight metrics hub for tracking system resources (CPU, RAM, disk I/O, Docker stats) across multiple hosts. It provides a simpler, more resource-efficient alternative to the Prometheus/Grafana stack for "set and forget" observability.

---

## 1. Contents

```
beszel/
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
3. Access UI at `http://localhost:8090`
4. Create your admin account
5. Add agents to monitored hosts (see Agent Deployment)

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `BESZEL_PORT` | 8090 | Web UI port |

---

## 5. Architecture

Beszel uses a hub-and-agent architecture:

| Component | Purpose |
|-----------|---------|
| Hub | Central dashboard, data storage, alerting |
| Agent | Lightweight collector deployed on each host |

The hub stores historical metrics and provides visualization. Agents are minimal processes that report to the hub.

---

## 6. Agent Deployment

After starting the hub, deploy agents on each monitored host:

```bash
docker run -d \
  --name beszel-agent \
  --restart unless-stopped \
  --network host \
  -v /var/run/docker.sock:/var/run/docker.sock:ro \
  -e KEY="<your-key-from-hub>" \
  -e HUB="<hub-ip>:45876" \
  henrygd/beszel-agent
```

Get the `KEY` from the hub UI when adding a new system.

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `beszel_data` | Metrics database, configuration |

---

## 8. Metrics Collected

- CPU usage (per core and aggregate)
- Memory usage and swap
- Disk I/O and space
- Network throughput
- Docker container stats
- System temperature (where available)

---

## 9. Comparison to Alternatives

| Feature | Beszel | Prometheus+Grafana |
|---------|--------|-------------------|
| Setup complexity | Minimal | Complex |
| Resource usage | ~50MB RAM | ~500MB+ RAM |
| Dashboard customization | Basic | Extensive |
| Long-term storage | Built-in | Requires config |
| Alerting | Basic | Advanced |

Beszel is ideal for homelabs and small deployments. For enterprise observability, consider Prometheus/Grafana.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/henrygd/beszel) | Source code |
| [Monitoring & Logging](../README.md) | Parent category |
| [Grafana](../grafana/README.md) | Full-featured dashboards |
| [Prometheus](../Prometheus/README.md) | Time-series database |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
