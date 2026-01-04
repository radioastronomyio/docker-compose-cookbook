<!--
---
title: "Wyoming Whisper"
description: "Home Assistant Wyoming protocol STT server with GPU acceleration"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/audio-intelligence
  - application: wyoming-whisper
---
-->

# Wyoming Whisper

Speech-to-text server implementing the Wyoming protocol for Home Assistant voice satellite integration, enabling high-fidelity local voice command processing with GPU acceleration.

---

## 1. Overview

Wyoming is the protocol used by Home Assistant for voice assistant satellites. Running Whisper STT on a GPU (rather than a Raspberry Pi) enables using larger, more accurate models with near-zero latency.

| Attribute | Value |
|-----------|-------|
| **Image** | `rhasspy/wyoming-whisper` |
| **Ports** | 10300 (Wyoming protocol) |
| **GPU Required** | Optional but recommended |
| **VRAM** | 2-6GB depending on model |
| **Documentation** | [github.com/rhasspy/wyoming-whisper](https://github.com/rhasspy/wyoming-whisper) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | Recommended for medium/large models |
| Home Assistant | For voice pipeline integration |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/audio-intelligence/wyoming-whisper

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Service available at localhost:10300
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `WHISPER_MODEL` | `medium` | Model size (tiny/base/small/medium/large) |
| `WHISPER_LANGUAGE` | `en` | Target language code |

### 4.2 Model Selection

| Model | VRAM | Use Case |
|-------|------|----------|
| `tiny` | ~1GB | Resource-constrained, simple commands |
| `small` | ~2GB | Good balance for most use cases |
| `medium` | ~5GB | Higher accuracy, recommended with GPU |
| `large` | ~6GB | Best accuracy, requires GPU |

---

## 5. Home Assistant Integration

1. Go to Settings → Devices & Services
2. Add Integration: Wyoming Protocol
3. Host: `your-docker-host-ip`
4. Port: `10300`

Configure in voice pipeline:

1. Settings → Voice Assistants
2. Add or edit assistant
3. Set Speech-to-Text: Wyoming Whisper

---

## 6. Performance Comparison

| Environment | Model | Latency |
|-------------|-------|---------|
| Raspberry Pi 4 | tiny | ~2-3s |
| CPU (x86) | small | ~1-2s |
| RTX 3080 | medium | ~0.2-0.5s |
| RTX 3080 | large | ~0.3-0.6s |

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./wyoming-data` | Downloaded model weights |

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Audio Intelligence README](../README.md) | Parent category |
| [Faster Whisper](../faster-whisper/README.md) | API-based alternative |
| [Home Assistant](../../../../home-automation/README.md) | Integration target |
