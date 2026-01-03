<!--
---
title: "Image Generation"
description: "Docker recipes for AI image generation and Stable Diffusion interfaces"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: image-generation
---
-->

# Image Generation

Docker Compose recipes for AI-powered image generation. These tools run Stable Diffusion, SDXL, Flux, and other diffusion models locally with GPU acceleration.

---

## 1. Contents

```
image-generation/
├── automatic1111/    # Classic SD WebUI with extensive extensions
├── comfyui/          # Node-based workflow engine
├── fooocus/          # Simplified Midjourney-like experience
├── invokeai/         # Professional creative studio
├── swarmui/          # Distributed inference orchestration
└── README.md         # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [automatic1111/](automatic1111/README.md) | Stable Diffusion WebUI with massive extension ecosystem | ✅ Active |
| [comfyui/](comfyui/README.md) | Node-based workflows with efficient VRAM usage | ✅ Active |
| [fooocus/](fooocus/README.md) | Simplified SDXL with automatic prompt enhancement | ✅ Active |
| [invokeai/](invokeai/README.md) | Unified Canvas for professional inpainting/outpainting | ✅ Active |
| [swarmui/](swarmui/README.md) | Multi-backend orchestration and render farm | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Maximum extension support | Automatic1111 |
| Reproducible workflows, efficiency | ComfyUI |
| Quick results, minimal config | Fooocus |
| Professional design work | InvokeAI |
| Multi-GPU distribution | SwarmUI |

---

## 4. Hardware Requirements

All image generation tools require a GPU. CPU-only operation is not practical.

| Tool | Minimum VRAM | SDXL Capable | Flux Capable |
|------|--------------|--------------|--------------|
| Automatic1111 | 8GB | 12GB+ | 16GB+ |
| ComfyUI | 6GB | 10GB+ | 12GB+ |
| Fooocus | 8GB | 10GB+ | N/A |
| InvokeAI | 8GB | 12GB+ | 16GB+ |
| SwarmUI | 8GB | 12GB+ | 16GB+ |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [LLM Inference](../llm-inference/README.md) | Text models for prompt enhancement |
