<!--
---
title: "Faster Whisper Server"
description: "OpenAI-compatible GPU-accelerated speech-to-text API server"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/audio-intelligence
  - application: faster-whisper
---
-->

# Faster Whisper Server

High-performance speech-to-text server wrapping the CTranslate2-optimized Whisper implementation in an OpenAI-compatible API, enabling drop-in replacement for cloud transcription.

---

## 1. Overview

Faster Whisper uses CTranslate2 for significantly faster inference compared to the original Whisper implementation. On an RTX 3080, the large-v3 model transcribes audio faster than real-time.

| Attribute | Value |
|-----------|-------|
| **Image** | `fedirz/faster-whisper-server:latest-cuda` |
| **Ports** | 8000 (API) |
| **GPU Required** | Yes |
| **VRAM** | 2-6GB depending on model size |
| **Documentation** | [github.com/fedirz/faster-whisper-server](https://github.com/fedirz/faster-whisper-server) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | 4GB+ VRAM for large models |
| NVIDIA Container Toolkit | For GPU passthrough |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/audio-intelligence/faster-whisper

# Start the service (downloads model on first run)
docker compose up -d

# Test transcription
curl -X POST http://localhost:8000/v1/audio/transcriptions \
  -F file=@audio.mp3 \
  -F model=large-v3
```

---

## 4. Configuration

### 4.1 Model Selection

| Model | VRAM | Speed | Accuracy |
|-------|------|-------|----------|
| `tiny` | ~1GB | Fastest | Lower |
| `base` | ~1GB | Fast | Good |
| `small` | ~2GB | Medium | Better |
| `medium` | ~5GB | Slower | High |
| `large-v3` | ~6GB | Slowest | Best |

Configure via API request or environment variable.

---

## 5. API Compatibility

The server implements the OpenAI Whisper API specification:

```python
import openai

client = openai.OpenAI(
    api_key="not-needed",
    base_url="http://localhost:8000/v1"
)

transcript = client.audio.transcriptions.create(
    model="large-v3",
    file=open("audio.mp3", "rb")
)
```

---

## 6. Performance

On RTX 3080 with large-v3:

| Audio Length | Transcription Time |
|--------------|-------------------|
| 1 minute | ~8 seconds |
| 10 minutes | ~60 seconds |
| 1 hour | ~6 minutes |

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./whisper-cache` | Downloaded model weights |

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Audio Intelligence README](../README.md) | Parent category |
| [Wyoming Whisper](../wyoming-whisper/README.md) | Home Assistant integration |
| [Open WebUI](../../chat-interfaces/open-webui/README.md) | Uses for voice input |
