<!--
---
title: "Hoarder Docker Setup"
description: "Docker Compose deployment for Hoarder AI-enhanced bookmarking"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: hoarder
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[GitHub Repository](https://github.com/hoarder-app/hoarder)"
---
-->

# Hoarder Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Hoarder is an AI-enhanced bookmarking application that organizes links, notes, and images with automatic tagging. It uses local LLMs to categorize content, providing a self-hosted alternative to services like Pocket or Raindrop.

---

## 1. Contents

```
hoarder/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- (Optional) Ollama for AI tagging

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secrets: `openssl rand -base64 32` (twice)
3. Set `NEXTAUTH_SECRET` and `MEILI_MASTER_KEY`
4. Run `docker compose up -d`
5. Access UI at `http://localhost:3000`
6. Create your account

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `HOARDER_PORT` | 3000 | Web UI port |
| `NEXTAUTH_URL` | http://localhost:3000 | Public URL |
| `NEXTAUTH_SECRET` | - | Auth encryption key |
| `MEILI_MASTER_KEY` | - | Search encryption key |
| `OLLAMA_BASE_URL` | - | Ollama URL for AI tagging |
| `INFERENCE_MODEL` | - | LLM model name |

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `web` | Next.js application |
| `chrome` | Headless browser for link screenshots |
| `meilisearch` | Full-text search engine |

---

## 6. AI Tagging

Connect to Ollama for automatic content categorization:

1. Ensure Ollama is running: `ollama serve`
2. Set `OLLAMA_BASE_URL=http://host.docker.internal:11434`
3. Set `INFERENCE_MODEL=llama3.2`
4. Restart Hoarder

Hoarder analyzes saved content and suggests relevant tags automatically.

---

## 7. Features

| Feature | Description |
|---------|-------------|
| Bookmarks | Save and organize links |
| Notes | Quick text notes |
| Images | Save and tag images |
| Auto-tagging | AI-powered categorization |
| Full-text Search | Find content across all items |
| Browser Extension | Quick capture from any page |
| Mobile Apps | iOS and Android support |

---

## 8. Data Persistence

| Volume | Purpose |
|--------|---------|
| `hoarder-data` | User data, bookmarks, uploads |
| `meilisearch-data` | Search index |

---

## 9. Browser Extension

Install the browser extension for one-click saving:

1. Go to Settings in Hoarder
2. Find browser extension links
3. Install for Chrome/Firefox
4. Configure extension with your server URL

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/hoarder-app/hoarder) | Source code |
| [Personal Utilities](../README.md) | Parent category |
| [Ollama](../../ai-ml/llm-inference/ollama/README.md) | AI backend |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
