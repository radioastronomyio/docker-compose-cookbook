<!--
---
title: "IT-Tools Docker Setup"
description: "Docker Compose deployment for IT-Tools developer utilities"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: it-tools
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://github.com/CorentinTh/it-tools)"
---
-->

# IT-Tools Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

IT-Tools aggregates useful developer utilities — JWT parser, SQL formatter, Base64 encoder, Crontab generator, hash generators, and more — into a single self-hosted interface. The primary ROI is security: sensitive data (API keys, tokens, hashes) never leaves your local network.

---

## 1. Contents

```
it-tools/
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

1. Copy `.env.example` to `.env` (no required variables)
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:8082`

---

## 4. Configuration

No configuration required. IT-Tools runs as a static web application with all processing done client-side.

### Security Benefits

Developers often paste sensitive data (API keys, tokens, hashes) into public web tools to decode or format them. Self-hosting IT-Tools ensures that this sensitive data never leaves the local network — creating a "Safe Harbor" for operational data manipulation.

---

## 5. Data Persistence

No server-side persistence required. All processing is client-side.

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8082 | TCP | Web UI |

---

## 7. Available Tools

IT-Tools includes 80+ utilities across categories: crypto/hashing, encoding/decoding, text manipulation, network utilities, date/time tools, development helpers, and more.

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/CorentinTh/it-tools) | Source code |
| [Personal Utilities](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
