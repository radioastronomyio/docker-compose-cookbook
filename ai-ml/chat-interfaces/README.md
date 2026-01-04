<!--
---
title: "Chat Interfaces"
description: "Docker recipes for LLM chat frontends and orchestration layers"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: chat-interfaces
---
-->

# Chat Interfaces

Docker Compose recipes for web-based chat interfaces that connect to LLM inference backends. These provide user-friendly frontends for interacting with local models.

---

## 1. Contents

```
chat-interfaces/
├── open-webui/       # Full-featured Ollama/OpenAI frontend
├── librechat/        # Multi-provider unified interface
├── anythingllm/      # Desktop RAG solution
├── privategpt/       # Privacy-first document analysis
└── README.md         # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [open-webui/](open-webui/README.md) | Feature-rich chat UI with RAG and user management | ✅ Active |
| [librechat/](librechat/README.md) | Unified frontend for multiple LLM providers | ✅ Active |
| [anythingllm/](anythingllm/README.md) | Self-contained RAG-in-a-box solution | ✅ Active |
| [privategpt/](privategpt/README.md) | Offline, privacy-centric document RAG | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Ollama frontend with RAG | Open WebUI |
| Multiple providers (local + cloud) | LibreChat |
| Simple document Q&A | AnythingLLM |
| Air-gapped / privacy-critical | PrivateGPT |

---

## 4. Feature Comparison

| Feature | Open WebUI | LibreChat | AnythingLLM | PrivateGPT |
|---------|------------|-----------|-------------|------------|
| Multi-user | ✅ | ✅ | ✅ | ❌ |
| Built-in RAG | ✅ | Plugin | ✅ | ✅ |
| OpenAI API | ✅ | ✅ | ✅ | ✅ |
| Ollama native | ✅ | ✅ | ✅ | ✅ |
| Code execution | ❌ | ✅ | ✅ | ❌ |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [LLM Inference](../llm-inference/README.md) | Backend engines these connect to |
| [Vector Databases](../../databases/vector/README.md) | RAG storage backends |
