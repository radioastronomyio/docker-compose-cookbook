<!--
---
title: "AnythingLLM"
description: "Self-contained RAG-in-a-box solution with built-in vector database and document processing"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/chat-interfaces
  - application: anythingllm
---
-->

# AnythingLLM

Self-contained "RAG-in-a-box" solution that manages its own vector database (LanceDB), embedding models, and document processing pipeline, focusing on ease of use for document interaction.

---

## 1. Overview

Unlike pure chat frontends, AnythingLLM performs significant data processing internally. It handles document ingestion, embedding generation, and retrieval without requiring external vector databases, making it ideal for quick RAG deployments.

| Attribute | Value |
|-----------|-------|
| **Image** | `mintplexlabs/anythingllm:master` |
| **Ports** | 3001 (Web UI) |
| **GPU Required** | Optional (accelerates embedding generation) |
| **Documentation** | [docs.anythingllm.com](https://docs.anythingllm.com/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | Optional, for accelerated embeddings |
| Backend | Ollama or OpenAI-compatible API |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/chat-interfaces/anythingllm

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:3001
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `STORAGE_DIR` | `/app/server/storage` | Persistent data location |
| `SERVER_PORT` | `3001` | Application port |
| `JWT_SECRET` | Required | Authentication token secret |

### 4.2 LLM Backend Connection

Configure your LLM backend through the web UI after first launch. AnythingLLM supports:

- Ollama (local)
- OpenAI API
- Azure OpenAI
- Anthropic Claude
- Local llama.cpp

---

## 5. Features

| Feature | Description |
|---------|-------------|
| Built-in Vector DB | LanceDB for embedding storage |
| Document Processing | PDF, DOCX, TXT, MD ingestion |
| Multi-user | Team workspace support |
| Code Execution | Sandboxed code interpreter |

---

## 6. Capabilities

The `cap_add: SYS_ADMIN` permission enables:

- Sandboxed code execution
- Complex document parsing
- Browser-based scraping

Remove if not using these features.

---

## 7. Volumes

| Volume | Purpose |
|--------|---------|
| `anythingllm_storage` | Documents, embeddings, conversations |
| `./.env` | Runtime configuration |

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Chat Interfaces README](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Recommended backend |
| [Vector Databases](../../../../databases/vector/README.md) | Alternative RAG storage |
