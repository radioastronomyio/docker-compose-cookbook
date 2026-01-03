<!--
---
title: "InvokeAI"
description: "Professional creative studio with unified canvas for inpainting and outpainting"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/image-generation
  - application: invokeai
---
-->

# InvokeAI

Professional-grade image generation studio featuring a "Unified Canvas" for infinite outpainting, precision inpainting, and a polished workflow designed for creative professionals.

---

## 1. Overview

InvokeAI positions itself as a design tool rather than just a generator. The Unified Canvas provides infinite workspace for compositing, extending images in any direction, and precise region-based generation.

| Attribute | Value |
|-----------|-------|
| **Image** | `ghcr.io/invoke-ai/invokeai:latest` |
| **Ports** | 9090 (Web UI) |
| **GPU Required** | Yes |
| **VRAM** | 8GB minimum, 12GB recommended |
| **Documentation** | [invoke-ai.github.io/InvokeAI](https://invoke-ai.github.io/InvokeAI/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | 8GB+ VRAM |
| NVIDIA Container Toolkit | For GPU passthrough |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/image-generation/invokeai

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:9090
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `INVOKEAI_ROOT` | `/invokeai` | Application root directory |
| `GPU_DRIVER` | `cuda` | GPU driver selection |
| `HUGGINGFACE_TOKEN` | (optional) | For automated model downloads |

---

## 5. Features

| Feature | Description |
|---------|-------------|
| Unified Canvas | Infinite workspace for compositing |
| Inpainting | Precise mask-based regeneration |
| Outpainting | Extend images in any direction |
| Node Editor | Advanced workflow graphs |
| Model Manager | Built-in download and conversion |

---

## 6. Model Management

InvokeAI includes a built-in model manager accessible from the UI:

1. Click the model icon in the sidebar
2. Browse HuggingFace or CivitAI
3. Download directly to your instance

Alternatively, place models in:

```
invokeai_root/
├── models/
│   ├── sd-1/
│   ├── sdxl/
│   └── controlnet/
```

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./invokeai_root` | Complete application state, models, outputs |

---

## 8. TensorRT Acceleration

InvokeAI supports TensorRT for faster inference if the CUDA image includes the necessary libraries. Performance gains of 30-50% are typical on RTX 30-series cards.

---

## 9. Related

| Document | Relationship |
|----------|--------------|
| [Image Generation README](../README.md) | Parent category |
| [ComfyUI](../comfyui/README.md) | Node-based alternative |
| [Automatic1111](../automatic1111/README.md) | Extension-focused alternative |
