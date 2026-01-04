<!--
---
title: "Open WebUI"
description: "Feature-rich chat interface for Ollama and OpenAI-compatible APIs with RAG support"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/chat-interfaces
  - application: open-webui
---
-->

# Open WebUI

Feature-rich web interface for interacting with LLMs via Ollama or OpenAI-compatible APIs, with built-in RAG capabilities, user management, and local Whisper transcription.

---

## 1. Overview

Open WebUI (formerly Ollama WebUI) provides a polished chat experience with advanced features including document upload for RAG, conversation history, user authentication, and GPU-accelerated local embedding generation.

| Attribute | Value |
|-----------|-------|
| **Image** | `ghcr.io/open-webui/open-webui:cuda` |
| **Ports** | 3000 (Web UI) |
| **GPU Required** | Optional (for local embeddings/Whisper) |
| **Documentation** | [docs.openwebui.com](https://docs.openwebui.com/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | Optional, enables local embeddings and Whisper |
| Backend | Ollama or OpenAI-compatible API running |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/chat-interfaces/open-webui

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:3000
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `OLLAMA_BASE_URL` | `http://host.docker.internal:11434` | Ollama API endpoint |
| `WEBUI_AUTH` | `true` | Enable authentication |
| `ENABLE_SIGNUP` | `false` | Allow new user registration |
| `WEBUI_SECRET_KEY` | Required | JWT signing key |
| `ENABLE_OPENAI_API` | `false` | Enable OpenAI API support |

### 4.2 Backend Connection

The `extra_hosts` configuration maps `host.docker.internal` to the Docker gateway, allowing the container to reach services on the host machine (like Ollama).

---

## 5. GPU Acceleration

The CUDA image enables:

- **Local embeddings**: Accelerate RAG document ingestion
- **Whisper transcription**: Voice-to-text for audio uploads
- **Faster response**: Reduced latency for embedding queries

Remove the `deploy` section to run CPU-only.

---

## 6. Volumes

| Volume | Purpose |
|--------|---------|
| `openwebui_data` | User data, conversations, uploaded documents |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Chat Interfaces README](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Recommended backend |
| [Vector Databases](../../../../databases/vector/README.md) | External RAG storage |
