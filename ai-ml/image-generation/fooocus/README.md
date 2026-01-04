<!--
---
title: "Fooocus"
description: "Simplified SDXL interface designed for Midjourney-like ease of use"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/image-generation
  - application: fooocus
---
-->

# Fooocus

Streamlined SDXL image generation that automates complex prompting and style parameter selection to achieve "Midjourney-like" results with minimal user input.

---

## 1. Overview

Fooocus strips away complexity, providing a clean interface where users describe what they want and the system handles the technical details. Optimized specifically for SDXL with proprietary sampling methods.

| Attribute | Value |
|-----------|-------|
| **Image** | `ghcr.io/lllyasviel/fooocus:latest` |
| **Ports** | 7865 (Web UI) |
| **GPU Required** | Yes |
| **VRAM** | 8GB minimum |
| **Documentation** | [github.com/lllyasviel/Fooocus](https://github.com/lllyasviel/Fooocus) |

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
cd ai-ml/image-generation/fooocus

# Configure environment
cp .env.example .env

# Start the service (downloads ~6GB of models on first run)
docker compose up -d

# Access UI
open http://localhost:7865
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CMD_ARGS` | `--listen` | Command line arguments |
| `DATADIR` | `/content/data` | Data directory path |

### 4.2 Presets

Launch in specific modes using presets:

| Preset | Use Case |
|--------|----------|
| `--preset anime` | Optimized for anime/illustration |
| `--preset realistic` | Photorealistic generation |
| (default) | Balanced for general use |

---

## 5. Default Models

Fooocus downloads JuggernautXL as the default checkpoint on first launch. Additional models can be placed in:

```
fooocus-data/
├── models/
│   ├── checkpoints/
│   ├── loras/
│   └── styles/
```

---

## 6. Volumes

| Path | Purpose |
|------|---------|
| `./fooocus-data` | Models, outputs, configuration |

---

## 7. Performance

On RTX 3080 (12GB):

- **Generation time**: ~15-20 seconds at 1024x1024
- **Batch processing**: Supports up to 8 images
- **Upscaling**: Built-in 2x upscaler

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Image Generation README](../README.md) | Parent category |
| [ComfyUI](../comfyui/README.md) | Advanced alternative |
| [Automatic1111](../automatic1111/README.md) | Feature-rich alternative |
