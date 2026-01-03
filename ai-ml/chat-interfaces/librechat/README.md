<!--
---
title: "LibreChat"
description: "Unified multi-provider chat frontend supporting Ollama, OpenAI, Azure, and Anthropic"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/chat-interfaces
  - application: librechat
---
-->

# LibreChat

Unified chat interface that aggregates multiple AI providers—Ollama, OpenAI, Azure, Anthropic—into a single cohesive experience with plugins, code interpretation, and file analysis.

---

## 1. Overview

LibreChat excels at unifying disparate model sources into one interface. The `librechat.yaml` configuration file defines custom endpoints, allowing seamless switching between local Llama models and cloud-based GPT-4 within the same conversation.

| Attribute | Value |
|-----------|-------|
| **Image** | `ghcr.io/danny-avila/librechat-dev:latest` |
| **Ports** | 3080 (Web UI) |
| **GPU Required** | No (connects to external backends) |
| **Documentation** | [librechat.ai/docs](https://www.librechat.ai/docs) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| MongoDB | Included in stack |
| Backend | Ollama, OpenAI API, or other compatible endpoint |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/chat-interfaces/librechat

# Configure environment
cp .env.example .env

# Create librechat.yaml for custom endpoints
# See Configuration section below

# Start the stack
docker compose up -d

# Access UI
open http://localhost:3080
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CREDS_KEY` | Required | Encryption key for credentials |
| `CREDS_IV` | Required | Initialization vector for encryption |
| `JWT_SECRET` | Required | JWT token signing secret |
| `ENDPOINTS` | `custom` | Enabled endpoint types |

### 4.2 Custom Endpoints (librechat.yaml)

Create a `librechat.yaml` file to define local Ollama endpoints:

```yaml
version: 1.0.0
cache: true
endpoints:
  custom:
    - name: "Local Ollama"
      apiKey: "ollama"
      baseURL: "http://host.docker.internal:11434/v1"
      models:
        default: ["llama3:8b", "mistral:7b"]
        fetch: true
```

Mount this file via the volumes section.

---

## 5. Architecture

LibreChat requires MongoDB for data persistence. The stack includes:

- **librechat**: Main application server
- **mongodb**: Conversation and user data storage

Optional: Add MeiliSearch for conversation search functionality.

---

## 6. Volumes

| Volume | Purpose |
|--------|---------|
| `mongo_data` | MongoDB database files |
| `./librechat.yaml` | Custom endpoint configuration |
| `./images` | User-uploaded images |
| `./logs` | Application logs |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Chat Interfaces README](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Local backend option |
| [MongoDB](../../../../databases/document/README.md) | Database dependency |
