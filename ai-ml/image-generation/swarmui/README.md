<!--
---
title: "SwarmUI"
description: "Distributed inference orchestration for managing multiple image generation backends"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/image-generation
  - application: swarmui
---
-->

# SwarmUI

Orchestration layer for managing multiple image generation backends (ComfyUI, A1111), enabling distributed rendering and unified model management across instances.

---

## 1. Overview

SwarmUI acts as a central hub that can spawn and manage backend inference engines. For single-GPU setups, it serves as a superior interface that abstracts backend complexity while providing advanced queue management.

| Attribute | Value |
|-----------|-------|
| **Image** | `ghcr.io/mcmonkeyprojects/swarmui:latest` |
| **Ports** | 7801 (Web UI) |
| **GPU Required** | Yes |
| **VRAM** | Depends on backend configuration |
| **Documentation** | [github.com/mcmonkeyprojects/SwarmUI](https://github.com/mcmonkeyprojects/SwarmUI) |

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
cd ai-ml/image-generation/swarmui

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI (accept EULA on first launch)
open http://localhost:7801
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `ACCEPT_EULA` | `true` | Accept the license agreement |
| `SWARM_NO_AUTO_INSTALL` | `false` | Disable automatic backend setup |

---

## 5. Architecture

SwarmUI can operate in two modes:

### 5.1 Self-Contained

The default configuration spawns internal ComfyUI backends automatically. No additional setup required.

### 5.2 External Backends

Configure SwarmUI to connect to existing ComfyUI or A1111 instances running elsewhere on your network for distributed rendering.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Queue Management | Batch processing with priority queues |
| Multi-Backend | Distribute load across multiple GPUs/machines |
| Model Sync | Unified model management across backends |
| Workflow Library | Save and share generation presets |

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./swarm_data` | Application state, queues, settings |
| `./swarm_models` | Shared model storage |

---

## 8. Multi-GPU Setup

For systems with multiple GPUs, configure multiple backends in the SwarmUI settings, assigning each to a specific GPU via `CUDA_VISIBLE_DEVICES`.

---

## 9. Related

| Document | Relationship |
|----------|--------------|
| [Image Generation README](../README.md) | Parent category |
| [ComfyUI](../comfyui/README.md) | Supported backend |
| [Automatic1111](../automatic1111/README.md) | Supported backend |
