<!--
---
title: "Text Generation WebUI Docker Setup"
description: "Docker Compose deployment for Oobabooga's Text Generation WebUI"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: llm-inference
  - tech: text-generation-webui
  - tech: oobabooga
related_documents:
  - "[LLM Inference README](../README.md)"
  - "[Official Repo](https://github.com/oobabooga/text-generation-webui)"
---
-->

# Text Generation WebUI Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Text Generation WebUI (Oobabooga) is a research-oriented Gradio interface providing granular control over sampling parameters and supporting multiple quantization backends including ExLlamaV2, GPTQ, and AWQ.

---

## 1. Contents

```
text-generation-webui/
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
2. Create directories: `mkdir -p ./textgen-data ./textgen-models`
3. Run `docker compose up -d`
4. Access WebUI at `http://localhost:7860`
5. Access API at `http://localhost:5000`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `CLI_ARGS` | (see compose) | Command line arguments |
| `CUDA_VISIBLE_DEVICES` | 0 | GPU selection |

### Key CLI Arguments

| Argument | Purpose |
|----------|---------|
| `--listen` | Bind to all interfaces |
| `--api` | Enable API endpoint |
| `--xformers` | Memory-efficient attention |
| `--n-gpu-layers 128` | GPU layer offloading |

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./textgen-data` | Character configs, extensions |
| `./textgen-models` | Model weights |

---

## 6. Shared Memory

The container requires elevated shared memory (`shm_size: 16gb`) because PyTorch dataloaders use `/dev/shm` for inter-process communication. The Docker default of 64MB is insufficient for large models.

---

## 7. Model Loading

1. Download GGUF/GPTQ/AWQ models to `./textgen-models`
2. Access WebUI → Model tab
3. Select model and loader (llama.cpp, ExLlamaV2, etc.)
4. Adjust GPU layers based on VRAM
5. Click Load

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [GitHub Repository](https://github.com/oobabooga/text-generation-webui) | Upstream repo |
| [HuggingFace Models](https://huggingface.co/models) | Model downloads |
| [LLM Inference](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
