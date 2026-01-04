<!--
---
title: "ComfyUI"
description: "Node-based image generation workflow engine with superior VRAM efficiency"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/image-generation
  - application: comfyui
---
-->

# ComfyUI

Node-based Stable Diffusion interface offering reproducible workflows, modular architecture, and significantly lower VRAM overhead compared to traditional UIs.

---

## 1. Overview

ComfyUI has eclipsed Automatic1111 for power users due to its visual workflow system. Each generation is a graph of connected nodes, making complex pipelines reproducible and shareable.

| Attribute | Value |
|-----------|-------|
| **Image** | `yanwk/comfyui-boot:cu124` |
| **Ports** | 8188 (Web UI) |
| **GPU Required** | Yes |
| **VRAM** | 6GB minimum, 12GB for SDXL |
| **Documentation** | [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | 6GB+ VRAM |
| NVIDIA Container Toolkit | For GPU passthrough |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/image-generation/comfyui

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:8188
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `CLI_ARGS` | (empty) | Additional command line arguments |
| `COMFYUI_CLEAN_OUTPUTS` | `false` | Auto-clean old outputs |

### 4.2 VRAM Management

| Argument | Use Case |
|----------|----------|
| (none) | Default for 12GB+ cards |
| `--normalvram` | Safe mode for 10-12GB |
| `--lowvram` | For 6-8GB or multitasking |

---

## 5. Efficiency

ComfyUI's architecture loads only necessary model components into VRAM:

- **SDXL base**: ~6GB (vs ~10GB in A1111)
- **Refiner**: Loaded on demand
- **ControlNet**: Modular loading

This enables running SDXL on 8GB cards without medvram hacks.

---

## 6. Volumes

| Path | Purpose |
|------|---------|
| `./comfyui-storage` | All application data including models, outputs, custom nodes |

### 6.1 Directory Structure

```
comfyui-storage/
├── ComfyUI/
│   ├── models/
│   │   ├── checkpoints/
│   │   ├── loras/
│   │   └── controlnet/
│   ├── output/
│   └── custom_nodes/
```

---

## 7. Custom Nodes

Install ComfyUI-Manager for easy node management:

1. Access the UI at http://localhost:8188
2. Click "Manager" in the menu
3. Install nodes from the marketplace

Or clone directly into `comfyui-storage/ComfyUI/custom_nodes/`.

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Image Generation README](../README.md) | Parent category |
| [Automatic1111](../automatic1111/README.md) | Traditional alternative |
| [SwarmUI](../swarmui/README.md) | Orchestration layer |
