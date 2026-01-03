<!--
---
title: "LocalAI Docker Setup"
description: "Docker Compose deployment for LocalAI OpenAI-compatible API"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: llm-inference
  - tech: localai
related_documents:
  - "[LLM Inference README](../README.md)"
  - "[Official Docs](https://localai.io/)"
---
-->

# LocalAI Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

LocalAI is a comprehensive OpenAI API drop-in replacement supporting LLMs, image generation, audio transcription, and embeddings. It aims to be a "Swiss Army Knife" for local AI inference.

---

## 1. Contents

```
localai/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 8GB+ VRAM
- NVIDIA Container Toolkit

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Create models directory: `mkdir -p ./localai_models`
3. Run `docker compose up -d`
4. Access API at `http://localhost:8080`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `THREADS` | 8 | CPU threads (set to physical cores) |
| `CONTEXT_SIZE` | 4096 | Default context window |
| `GPU_ACCELERATION` | true | Enable CUDA acceleration |
| `API_KEY` | (none) | Optional API key for security |
| `DEBUG` | false | Enable debug logging |

### Image Selection

The `aio-gpu-nvidia-cuda-12` image includes:
- CUDA 12 libraries
- Stable Diffusion support
- TTS capabilities
- All model backends

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./localai_models` | Model weights and configs |
| `./localai_images` | Generated images |

---

## 6. Model Configuration

LocalAI uses YAML configs in the models directory:

```yaml
# models/llama3.yaml
name: llama3
backend: llama-cpp
parameters:
  model: llama-3-8b-instruct.Q4_K_M.gguf
context_size: 4096
gpu_layers: 35
```

---

## 7. API Compatibility

LocalAI implements the OpenAI API specification:

```bash
# Chat completion
curl http://localhost:8080/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "llama3",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'

# Embeddings
curl http://localhost:8080/v1/embeddings \
  -d '{"model": "text-embedding-ada-002", "input": "Hello world"}'
```

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://localai.io/) | Upstream docs |
| [Model Gallery](https://localai.io/models/) | Pre-configured models |
| [LLM Inference](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
