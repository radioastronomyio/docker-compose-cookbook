<!--
---
title: "ChangeDetection.io Docker Setup"
description: "Docker Compose deployment for ChangeDetection.io website monitoring"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: automation-orchestration
  - tech: changedetection
related_documents:
  - "[Automation & Orchestration README](../README.md)"
  - "[GitHub Repository](https://github.com/dgtlmoon/changedetection.io)"
---
-->

# ChangeDetection.io Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

ChangeDetection.io monitors websites for changes and sends notifications when content updates. It's essential for tracking regulatory updates, pricing changes, product availability, or any web content you need to watch.

---

## 1. Contents

```
changedetection/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- ~1GB RAM for browser rendering

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access UI at `http://localhost:5000`
4. Add your first watch URL
5. Configure check frequency and notifications

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `CHANGEDETECTION_PORT` | 5000 | Web UI port |
| `PUID` | 1000 | User ID |
| `PGID` | 1000 | Group ID |
| `MAX_BROWSERS` | 4 | Concurrent browser instances |

---

## 5. Playwright Integration

Simple HTML scraping fails on modern JavaScript-heavy sites. The `playwright-chrome` sidecar provides:

- Full JavaScript execution
- DOM rendering before comparison
- Screenshot capture
- Proper handling of SPAs

This enables monitoring sites that load content dynamically.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Visual Diff | Side-by-side change comparison |
| CSS Selectors | Monitor specific page elements |
| XPath | Advanced element targeting |
| JSON/API | Monitor API endpoints |
| PDF Monitoring | Track PDF document changes |
| Screenshots | Visual change detection |
| Filters | Ignore dynamic content (ads, timestamps) |

---

## 7. Notification Channels

Supported notification methods:

- Email (SMTP)
- Discord, Slack, Telegram
- Pushover, Gotify, ntfy
- Webhooks (custom integrations)
- Apprise (70+ services)

---

## 8. Data Persistence

| Volume | Purpose |
|--------|---------|
| `changedetection-data` | Watch configurations, history, snapshots |

---

## 9. Use Cases

| Use Case | Configuration |
|----------|---------------|
| Price monitoring | CSS selector for price element |
| Stock alerts | Watch product availability div |
| Regulatory updates | Monitor government publication pages |
| Competitor tracking | Watch competitor feature pages |
| Job listings | Monitor career pages |

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/dgtlmoon/changedetection.io) | Source code |
| [Automation & Orchestration](../README.md) | Parent category |
| [n8n](../n8n/README.md) | Workflow automation on changes |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
