<!--
---
title: "SearXNG Docker Setup"
description: "Docker Compose deployment for SearXNG privacy-respecting metasearch engine"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: networking
  - tech: searxng
related_documents:
  - "[Networking README](../README.md)"
  - "[Official Docs](https://docs.searxng.org/)"
---
-->

# SearXNG Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

SearXNG is a privacy-respecting metasearch engine that aggregates results from multiple sources without tracking. It provides "internet access" for AI agents and RAG-Web workflows.

---

## 1. Contents

```
searxng/
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

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access search at `http://localhost:8080`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `SEARXNG_BASE_URL` | http://localhost:8080 | Public URL |
| `SEARXNG_SECRET_KEY` | - | Flask secret key |

### Custom Settings

Create `./searxng/settings.yml` to customize:

```yaml
general:
  instance_name: "My Search"

search:
  safe_search: 0
  default_lang: "en"

engines:
  - name: google
    disabled: false
  - name: duckduckgo
    disabled: false
```

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./searxng` | Configuration files |

---

## 6. AI Agent Integration

SearXNG can provide web search capabilities to AI agents:

| Platform | Configuration |
|----------|---------------|
| Open WebUI | Settings → Web Search → SearXNG URL |
| Dify | Add SearXNG as tool provider |
| n8n | HTTP Request node to SearXNG API |

### JSON API

```bash
curl "http://localhost:8080/search?q=test&format=json"
```

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.searxng.org/) | Upstream docs |
| [SearXNG GitHub](https://github.com/searxng/searxng) | Source code |
| [Open WebUI](../../ai-ml/chat-interfaces/open-webui/README.md) | AI frontend with web search |
| [Networking](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
