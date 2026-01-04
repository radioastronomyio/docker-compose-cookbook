<!--
---
title: "Audio Intelligence"
description: "Docker recipes for speech recognition and audio processing"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: audio-intelligence
---
-->

# Audio Intelligence

Docker Compose recipes for speech-to-text (ASR) and audio processing. These tools run OpenAI Whisper models locally with GPU acceleration for real-time transcription.

---

## 1. Contents

```
audio-intelligence/
├── faster-whisper/     # OpenAI-compatible transcription server
├── wyoming-whisper/    # Home Assistant voice integration
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [faster-whisper/](faster-whisper/README.md) | CTranslate2-optimized Whisper with OpenAI API | ✅ Active |
| [wyoming-whisper/](wyoming-whisper/README.md) | Wyoming protocol server for Home Assistant | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| General transcription API | Faster Whisper |
| Home Assistant voice commands | Wyoming Whisper |
| Podcast/video transcription | Faster Whisper |
| Smart home voice satellite | Wyoming Whisper |

---

## 4. Model Comparison

| Model | VRAM | Speed (RTX 3080) | Accuracy |
|-------|------|------------------|----------|
| tiny | 1GB | 32x realtime | Low |
| base | 1GB | 16x realtime | Fair |
| small | 2GB | 8x realtime | Good |
| medium | 5GB | 4x realtime | Very Good |
| large-v3 | 10GB | 2x realtime | Excellent |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [Home Automation](../../home-automation/README.md) | Voice assistant integration |
