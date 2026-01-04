<!--
---
title: "Perplexica Docker Setup"
description: "Docker Compose deployment for Perplexica AI answer engine"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: search-engines
  - tech: perplexica
related_documents:
  - "[AI Search Engines README](../README.md)"
  - "[GitHub Repository](https://github.com/ItzCrazyKns/Perplexica)"
---
-->

# Perplexica Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Perplexica is an open-source AI answer engine that aggregates web search results via SearXNG and synthesizes answers using local LLMs. It functions as a self-hosted alternative to Perplexity AI, keeping your queries private while leveraging web-scale information.

---

## 1. Contents

```
perplexica/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
├── config.toml         # Model configuration (create from template)
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ollama running on host (see [ollama](../../llm-inference/ollama/README.md))
- Models pulled: `llama3.2`, `nomic-embed-text`

---

## 3. Quick Start

1. Ensure Ollama is running: `ollama serve`
2. Pull required models: `ollama pull llama3.2 && ollama pull nomic-embed-text`
3. Copy `.env.example` to `.env`
4. Create `config.toml` (see Configuration section)
5. Run `docker compose up -d`
6. Access UI at `http://localhost:3000`

---

## 4. Configuration

### Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SEARXNG_PORT` | 4000 | SearXNG metasearch port |
| `PERPLEXICA_PORT` | 3000 | Web UI port |
| `PERPLEXICA_API_PORT` | 3001 | API/WebSocket port |
| `OLLAMA_PORT` | 11434 | Host Ollama port |

### config.toml

Create `config.toml` in the recipe directory:

```toml
[GENERAL]
PORT = 3001
SIMILARITY_MEASURE = "cosine"

[API_KEYS]
OPENAI = ""
GROQ = ""
ANTHROPIC = ""

[API_ENDPOINTS]
OLLAMA = "http://host.docker.internal:11434"
```

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `searxng` | Metasearch engine aggregating results from multiple providers |
| `perplexica` | Frontend + API that synthesizes search results with LLM |

Search queries hit the web via SearXNG, but answer synthesis happens locally on your GPU.

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `searxng-data` | SearXNG configuration and cache |
| `perplexica-data` | Chat history and user data |

---

## 7. Ollama Integration

Perplexica connects to Ollama via `host.docker.internal`. Ensure Ollama allows external connections:

```bash
# Set CORS for Docker access
OLLAMA_ORIGINS="*" ollama serve
```

Or in systemd service override:

```ini
[Service]
Environment="OLLAMA_ORIGINS=*"
```

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/ItzCrazyKns/Perplexica) | Source code |
| [AI Search Engines](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Required LLM backend |
| [SearXNG](../../../networking/searxng/README.md) | Standalone metasearch |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
