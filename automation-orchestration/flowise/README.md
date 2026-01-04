<!--
---
title: "Flowise Docker Setup"
description: "Docker Compose deployment for Flowise low-code LangChain builder"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: automation-orchestration
  - tech: flowise
related_documents:
  - "[Automation & Orchestration README](../README.md)"
  - "[Official Docs](https://docs.flowiseai.com/)"
---
-->

# Flowise Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Flowise provides a drag-and-drop interface specifically for building LangChain applications, making it easy to create RAG pipelines, chatbots, and AI agents without writing code.

---

## 1. Contents

```
flowise/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ollama or other LLM backend (for AI features)
- ChromaDB or other vector store (for RAG)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access UI at `http://localhost:3000`
4. Build your first chatflow

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PORT` | 3000 | Web UI port |
| `FLOWISE_USERNAME` | admin | UI username |
| `FLOWISE_PASSWORD` | password | UI password |
| `DATABASE_PATH` | /root/.flowise | SQLite database location |
| `APIKEY_PATH` | /root/.flowise | API keys storage |

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./flowise_data` | Flows, credentials, SQLite database |

---

## 6. Connecting to Local Services

When configuring nodes, use these addresses:

| Service | Address |
|---------|---------|
| Ollama | `http://host.docker.internal:11434` |
| ChromaDB | `http://host.docker.internal:8000` |
| Qdrant | `http://host.docker.internal:6333` |

---

## 7. Building a RAG Chatflow

1. Add **Document Loaders** (PDF, Text, etc.)
2. Add **Text Splitter** (Recursive Character)
3. Add **Embeddings** (Ollama Embeddings)
4. Add **Vector Store** (Chroma or Qdrant)
5. Add **Chat Model** (Ollama)
6. Add **Conversational Retrieval QA Chain**
7. Connect and deploy

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.flowiseai.com/) | Upstream docs |
| [Flowise GitHub](https://github.com/FlowiseAI/Flowise) | Source code |
| [Ollama](../../ai-ml/llm-inference/ollama/README.md) | LLM backend |
| [ChromaDB](../../databases/vector/chroma/README.md) | Vector store |
| [Automation & Orchestration](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
