<!--
---
title: "PrivateGPT"
description: "Privacy-first RAG solution for offline, air-gapped document analysis"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/chat-interfaces
  - application: privategpt
---
-->

# PrivateGPT

Privacy-centric RAG solution architected specifically for offline, air-gapped deployments. Includes a complete ingestion pipeline that runs locally, ensuring sensitive documents never leave the machine.

---

## 1. Overview

PrivateGPT prioritizes data sovereignty. The entire RAG pipeline—document ingestion, embedding generation, and retrieval—runs locally without external API calls. Supports multiple profiles for different backend configurations.

| Attribute | Value |
|-----------|-------|
| **Image** | `zylon/private-gpt:latest` |
| **Ports** | 8001 (Web UI / API) |
| **GPU Required** | Depends on profile |
| **Documentation** | [docs.privategpt.dev](https://docs.privategpt.dev/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| Backend | Ollama (for `ollama` profile) |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/chat-interfaces/privategpt

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:8001
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `PORT` | `8001` | Application port |
| `PGPT_PROFILES` | `ollama` | Backend profile selection |
| `PGPT_OLLAMA_API_BASE` | `http://host.docker.internal:11434` | Ollama endpoint |
| `PGPT_EMBEDDING_MODEL_NAME` | `nomic-embed-text` | Embedding model for RAG |

### 4.2 Profiles

| Profile | Description |
|---------|-------------|
| `ollama` | Delegates inference to external Ollama instance |
| `local` | Runs llama-cpp internally (higher resource usage) |
| `mock` | Testing mode with fake responses |

The `ollama` profile is recommended for RTX 3080 setups as it offloads inference while handling RAG logic internally.

---

## 5. Document Ingestion

Upload documents through the web UI or API. Supported formats:

- PDF
- DOCX, DOC
- TXT, MD
- HTML

Documents are processed locally and stored in `local_data/`.

---

## 6. Volumes

| Volume | Purpose |
|--------|---------|
| `./local_data` | Ingested documents and vector indices |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Chat Interfaces README](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Recommended backend |
| [Vector Databases](../../../../databases/vector/README.md) | Alternative storage |
