<!--
---
title: "AI & Machine Learning"
description: "LLM inference, AI tools, and machine learning platforms"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
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
└── README.md             # This file
```

---

## 2. Subdirectories

| Directory | Description |
|-----------|-------------|
| [llm-inference/](llm-inference/README.md) | Ollama, LocalAI, vLLM, Text Generation WebUI |
| [chat-interfaces/](chat-interfaces/README.md) | Open WebUI, LibreChat, AnythingLLM, PrivateGPT |
| [image-generation/](image-generation/README.md) | Automatic1111, ComfyUI, Fooocus, InvokeAI, SwarmUI |
| [audio-intelligence/](audio-intelligence/README.md) | Faster Whisper, Wyoming Whisper |
| [document-processing/](document-processing/README.md) | Stirling-PDF |

---

## 3. Quick Reference

| Need | Recommended Stack |
|------|-------------------|
| Local ChatGPT alternative | Ollama + Open WebUI |
| OpenAI API compatibility | LocalAI |
| Document Q&A (RAG) | Ollama + AnythingLLM + ChromaDB |
| Image generation | ComfyUI or Fooocus |
| Voice transcription | Faster Whisper |

---

## 4. Hardware Requirements

| Component | CPU-Only | GPU Required |
|-----------|----------|--------------|
| LLM inference (7B) | ✅ Slow | ✅ Fast |
| LLM inference (70B) | ❌ | ✅ 48GB+ VRAM |
| Image generation | ❌ | ✅ 8GB+ VRAM |
| Speech recognition | ✅ Slow | ✅ Fast |

---

## 5. GPU Configuration

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

## 6. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/vector/](../databases/vector/README.md) | Embedding storage for RAG |
| [automation-orchestration/](../automation-orchestration/README.md) | AI workflow tools (n8n, Flowise, Dify) |
