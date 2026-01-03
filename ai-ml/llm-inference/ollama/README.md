<!--
---
title: "Ollama Docker Setup"
description: "Docker Compose deployment for Ollama LLM inference"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: llm-inference
  - tech: ollama
related_documents:
  - "[LLM Inference README](../README.md)"
  - "[Official Docs](https://ollama.com/)"
---
-->

# Ollama Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Ollama is the de facto standard for local LLM inference, providing seamless model management via Modelfiles and abstracting the complexities of llama.cpp. It runs GGUF quantized models efficiently on consumer GPUs.

---

## 1. Contents

```
ollama/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 6GB+ VRAM (for 7B models)
- NVIDIA Container Toolkit

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Pull a model: `docker exec ollama ollama pull llama3.2`
4. Access API at `http://localhost:11434`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `OLLAMA_HOST` | 0.0.0.0 | Bind address |
| `OLLAMA_KEEP_ALIVE` | 24h | Time to keep models loaded in VRAM |
| `OLLAMA_NUM_PARALLEL` | 2 | Concurrent request handling |
| `OLLAMA_DEBUG` | false | Enable debug logging |

### Key Optimization Notes

- **OLLAMA_KEEP_ALIVE**: Default is 5 minutes. Setting to `24h` or `-1` (infinite) eliminates cold-start latency for dedicated servers.
- **OLLAMA_NUM_PARALLEL**: Safe at 2-4 for 7B models on 12GB VRAM. Keep at 1 for 70B models to preserve context window memory.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `ollama_storage` | Model weights and configuration |

---

## 6. Model Management

```bash
# Pull models
docker exec ollama ollama pull llama3.2
docker exec ollama ollama pull codellama
docker exec ollama ollama pull mistral

# List models
docker exec ollama ollama list

# Run interactive chat
docker exec -it ollama ollama run llama3.2
```

---

## 7. API Usage

```bash
# Generate completion
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?"
}'

# Chat completion
curl http://localhost:11434/api/chat -d '{
  "model": "llama3.2",
  "messages": [{"role": "user", "content": "Hello!"}]
}'
```

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://ollama.com/) | Upstream docs |
| [Model Library](https://ollama.com/library) | Available models |
| [Open WebUI](../chat-interfaces/open-webui/README.md) | Recommended frontend |
| [LLM Inference](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
