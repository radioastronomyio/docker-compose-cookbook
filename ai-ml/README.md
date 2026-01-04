<!--
---
title: "AI & Machine Learning"
description: "LLM inference, AI tools, and machine learning platforms"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
---
-->

# AI & Machine Learning

Docker Compose recipes for local LLM inference, AI tools, image generation, and machine learning platforms. All recipes are optimized for NVIDIA GPU acceleration via the Docker Deploy specification.

---

## 1. Contents

```
ai-ml/
├── llm-inference/        # LLM inference engines
├── chat-interfaces/      # Web UIs for LLM interaction
├── image-generation/     # Stable Diffusion and diffusion models
├── audio-intelligence/   # Speech-to-text and audio processing
├── document-processing/  # AI-enhanced document tools
├── rag-engines/          # RAG orchestration platforms
├── search-engines/       # AI-powered search
├── ai-agents/            # Autonomous AI agents
├── data-annotation/      # ML data labeling tools
└── README.md             # This file
```

---

## 2. Subdirectories

| Directory | Description | Recipes |
|-----------|-------------|---------|
| [llm-inference/](llm-inference/README.md) | LLM inference engines | Ollama, LocalAI, vLLM, Text-Generation-WebUI |
| [chat-interfaces/](chat-interfaces/README.md) | Web UIs for LLM interaction | Open WebUI, LibreChat, AnythingLLM, PrivateGPT |
| [image-generation/](image-generation/README.md) | Diffusion model interfaces | Automatic1111, ComfyUI, Fooocus, InvokeAI, SwarmUI |
| [audio-intelligence/](audio-intelligence/README.md) | Speech recognition | Faster Whisper, Wyoming Whisper |
| [document-processing/](document-processing/README.md) | Document manipulation | Stirling-PDF |
| [rag-engines/](rag-engines/README.md) | RAG orchestration | RAGFlow |
| [search-engines/](search-engines/README.md) | AI-powered search | Perplexica |
| [ai-agents/](ai-agents/README.md) | Autonomous agents | OpenHands |
| [data-annotation/](data-annotation/README.md) | ML data labeling | Label Studio, CVAT |

---

## 3. Recipe Count

| Subcategory | Count |
|-------------|-------|
| llm-inference | 4 |
| chat-interfaces | 4 |
| image-generation | 5 |
| audio-intelligence | 2 |
| document-processing | 1 |
| rag-engines | 1 |
| search-engines | 1 |
| ai-agents | 1 |
| data-annotation | 2 |
| **Total** | **21** |

---

## 4. Quick Reference

| Need | Recommended Stack |
|------|-------------------|
| Local ChatGPT alternative | Ollama + Open WebUI |
| OpenAI API compatibility | LocalAI |
| Document Q&A (RAG) | Ollama + AnythingLLM + ChromaDB |
| Enterprise RAG | RAGFlow |
| AI-powered search | Perplexica |
| Image generation | ComfyUI or Fooocus |
| Voice transcription | Faster Whisper |
| ML data labeling | Label Studio or CVAT |
| Autonomous coding agent | OpenHands |

---

## 5. Hardware Requirements

| Component | CPU-Only | GPU Required |
|-----------|----------|--------------|
| LLM inference (7B) | ✅ Slow | ✅ Fast |
| LLM inference (70B) | ❌ | ✅ 48GB+ VRAM |
| Image generation | ❌ | ✅ 8GB+ VRAM |
| Speech recognition | ✅ Slow | ✅ Fast |
| Data annotation | ✅ | Optional |

---

## 6. GPU Configuration

All GPU-accelerated recipes use the Docker Deploy specification:

```yaml
deploy:
  resources:
    reservations:
      devices:
        - driver: nvidia
          count: 1
          capabilities: [gpu]
```

Prerequisites:

- NVIDIA GPU with CUDA support
- NVIDIA Container Toolkit installed
- Docker Desktop with WSL2 (Windows) or native Docker (Linux)

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/vector/](../databases/vector/README.md) | Embedding storage for RAG |
| [automation-orchestration/](../automation-orchestration/README.md) | AI workflow tools (n8n, Flowise, Dify) |
