<!--
---
title: "AI & Machine Learning"
description: "LLM inference, AI tools, and machine learning platforms"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
---
-->

# AI & Machine Learning

Docker Compose recipes for local LLM inference, AI tools, image generation, and machine learning platforms.

---

## 1. Contents

```
ai-ml/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| ollama | Local LLM inference | High |
| open-webui | Chat UI for Ollama | High |
| localai | OpenAI-compatible API | High |
| text-generation-webui | Gradio UI for LLMs | Medium |
| comfyui | Node-based image generation | Medium |
| stable-diffusion-webui | Automatic1111 WebUI | Medium |
| jupyter | Jupyter notebooks | Medium |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Local ChatGPT alternative | Ollama + Open-WebUI |
| OpenAI API compatibility | LocalAI |
| Image generation | ComfyUI or SD-WebUI |
| Data science notebooks | Jupyter |

---

## 4. Hardware Considerations

| Component | CPU-Only | GPU Recommended |
|-----------|----------|-----------------|
| Ollama (7B models) | ✅ Slow | ✅ Fast |
| Ollama (70B models) | ❌ | ✅ Required |
| Stable Diffusion | ❌ | ✅ Required |
| ComfyUI | ❌ | ✅ Required |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/vector/](../databases/vector/README.md) | Embedding storage for RAG |
| [data-pipelines/](../data-pipelines/README.md) | ML workflow orchestration |
