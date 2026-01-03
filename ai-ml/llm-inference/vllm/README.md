<!--
---
title: "vLLM Docker Setup"
description: "Docker Compose deployment for vLLM high-throughput inference"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: llm-inference
  - tech: vllm
related_documents:
  - "[LLM Inference README](../README.md)"
  - "[Official Docs](https://docs.vllm.ai/)"
---
-->

# vLLM Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

vLLM is designed for maximum throughput using the PagedAttention algorithm. It is the most efficient engine for serving simultaneous requests in production environments.

---

## 1. Contents

```
vllm/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 16GB+ VRAM (Ampere or newer recommended)
- NVIDIA Container Toolkit
- HuggingFace account and token

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Set your HuggingFace token: `HF_TOKEN=hf_...`
3. Run `docker compose up -d`
4. Access OpenAI-compatible API at `http://localhost:8000`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `MODEL` | mistralai/Mistral-7B-Instruct-v0.2 | HuggingFace model ID |
| `GPU_MEMORY_UTILIZATION` | 0.85 | VRAM reservation (0.0-1.0) |
| `HF_TOKEN` | (required) | HuggingFace API token |

### Memory Utilization

- `0.9-0.95`: Aggressive, maximizes context length for single-task deployment
- `0.85`: Balanced, leaves headroom for other processes
- `0.7`: Conservative, allows concurrent GPU tasks

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./vllm-cache` | HuggingFace model cache |

---

## 6. API Usage

vLLM implements the OpenAI API specification:

```bash
curl http://localhost:8000/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{
    "model": "mistralai/Mistral-7B-Instruct-v0.2",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

---

## 7. Performance Notes

- PagedAttention enables efficient KV cache management
- Supports continuous batching for high throughput
- RTX 3080 (Ampere) is fully supported
- Best performance with native HuggingFace models (not GGUF)

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.vllm.ai/) | Upstream docs |
| [Supported Models](https://docs.vllm.ai/en/latest/models/supported_models.html) | Compatible models |
| [LLM Inference](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
