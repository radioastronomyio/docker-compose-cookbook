<!--
---
title: "Stable Diffusion WebUI (Automatic1111)"
description: "Feature-rich Stable Diffusion interface with extensive extension ecosystem"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/image-generation
  - application: automatic1111
---
-->

# Stable Diffusion WebUI (Automatic1111)

The most widely supported interface for Stable Diffusion, featuring a massive library of extensions, ControlNet support, and comprehensive sampling parameter controls.

---

## 1. Overview

Automatic1111 (A1111) remains the industry standard for Stable Diffusion despite newer alternatives. Its strength lies in the extensive extension ecosystem and granular control over generation parameters.

| Attribute | Value |
|-----------|-------|
| **Image** | `universalllamas/automatic1111:latest` |
| **Ports** | 7860 (Web UI) |
| **GPU Required** | Yes |
| **VRAM** | 8GB minimum, 12GB recommended for SDXL |
| **Documentation** | [github.com/AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui) |

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
cd ai-ml/image-generation/automatic1111

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI (first launch downloads models)
open http://localhost:7860
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CLI_ARGS` | See compose | Command line arguments |
| `PYTORCH_CUDA_ALLOC_CONF` | Memory settings | PyTorch memory allocation tuning |

### 4.2 CLI Arguments

| Argument | Purpose |
|----------|---------|
| `--listen` | Bind to all interfaces |
| `--xformers` | Memory-efficient attention (recommended) |
| `--medvram` | Reduce VRAM usage for 8-12GB cards |
| `--api` | Enable REST API |
| `--enable-insecure-extension-access` | Allow extension installation |

---

## 5. Memory Optimization

For RTX 3080 (12GB):

```yaml
environment:
  - CLI_ARGS=--listen --xformers --api
  - PYTORCH_CUDA_ALLOC_CONF=garbage_collection_threshold:0.6,max_split_size_mb:128
```

For 8GB cards, add `--medvram` to CLI_ARGS.

---

## 6. Volumes

| Path | Purpose |
|------|---------|
| `./sd-data` | Application data |
| `./sd-outputs` | Generated images |
| `./sd-models` | Checkpoints, LoRAs, VAEs |

---

## 7. Model Installation

Place models in the appropriate subdirectories:

```
sd-models/
├── Stable-diffusion/    # Main checkpoints (.safetensors)
├── Lora/                # LoRA adapters
├── VAE/                 # VAE models
└── ControlNet/          # ControlNet models
```

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Image Generation README](../README.md) | Parent category |
| [ComfyUI](../comfyui/README.md) | Node-based alternative |
| [Fooocus](../fooocus/README.md) | Simplified alternative |
