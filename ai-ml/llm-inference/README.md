<!--
---
title: "LLM Inference Engines"
description: "Docker recipes for local Large Language Model inference and serving"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: llm-inference
---
-->

# LLM Inference Engines

Docker Compose recipes for running Large Language Model inference locally. These engines load model weights into GPU VRAM and expose APIs for text generation.

---

## 1. Contents

```
llm-inference/
├── ollama/                    # Model management and inference
├── localai/                   # OpenAI API drop-in replacement
├── text-generation-webui/     # Gradio UI with multiple backends
├── vllm/                      # High-throughput production inference
└── README.md                  # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [ollama/](ollama/README.md) | GGUF model management with llama.cpp backend | ✅ Active |
| [localai/](localai/README.md) | OpenAI-compatible API supporting multiple architectures | ✅ Active |
| [text-generation-webui/](text-generation-webui/README.md) | Oobabooga's research-oriented WebUI | ✅ Active |
| [vllm/](vllm/README.md) | PagedAttention-based high-throughput serving | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Getting started, model exploration | Ollama |
| OpenAI API compatibility needed | LocalAI |
| Research, fine-grained sampling control | Text Generation WebUI |
| Production serving, high concurrency | vLLM |

---

## 4. Hardware Requirements

| Engine | Minimum VRAM | Recommended |
|--------|--------------|-------------|
| Ollama (7B Q4) | 6GB | 8GB+ |
| Ollama (70B Q4) | 40GB | 48GB+ |
| LocalAI | 8GB | 12GB+ |
| Text Gen WebUI | 8GB | 12GB+ |
| vLLM | 16GB | 24GB+ |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [Chat Interfaces](../chat-interfaces/README.md) | Frontend UIs for these engines |
| [Vector Databases](../../databases/vector/README.md) | Embedding storage for RAG |
