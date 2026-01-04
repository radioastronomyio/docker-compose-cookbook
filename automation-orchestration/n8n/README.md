<!--
---
title: "n8n Docker Setup"
description: "Docker Compose deployment for n8n workflow automation with AI capabilities"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: automation-orchestration
  - tech: n8n
related_documents:
  - "[Automation & Orchestration README](../README.md)"
  - "[Official Docs](https://docs.n8n.io/)"
---
-->

# n8n Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

n8n is a node-based workflow automation tool with deep LangChain integration, enabling AI-powered automations that connect to local LLMs via Ollama.

---

## 1. Contents

```
n8n/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ollama running locally (for AI features)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access UI at `http://localhost:5678`
4. Create your first workflow

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `N8N_HOST` | localhost | Hostname for n8n |
| `N8N_PORT` | 5678 | Web UI port |
| `N8N_PROTOCOL` | http | Protocol (http/https) |
| `WEBHOOK_URL` | http://localhost:5678/ | Base URL for webhooks |
| `N8N_GENAI_ENABLED` | true | Enable AI Assistant features |
| `GENERIC_TIMEZONE` | America/New_York | Timezone for scheduling |

### AI Integration

Setting `N8N_GENAI_ENABLED=true` unlocks the AI Assistant and LangChain nodes. Configure the Ollama node to point to `http://host.docker.internal:11434` to use local models.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `n8n_data` | Workflows, credentials, execution logs |

---

## 6. Connecting to Local LLMs

In n8n, create an Ollama credential with:
- **Base URL**: `http://host.docker.internal:11434`

Then use the "Ollama Chat Model" or "Ollama Embeddings" nodes in your AI workflows.

---

## 7. Example Workflows

- **RAG Pipeline**: Document ingestion → ChromaDB → LLM query
- **Email Summarizer**: Gmail trigger → Ollama summarization → Slack notification
- **Code Assistant**: Webhook → Code analysis → GitHub PR comment

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.n8n.io/) | Upstream docs |
| [Community Workflows](https://n8n.io/workflows/) | Template library |
| [Ollama](../../ai-ml/llm-inference/ollama/README.md) | LLM backend |
| [Automation & Orchestration](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
