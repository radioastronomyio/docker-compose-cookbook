<!--
---
title: "Frigate Docker Setup"
description: "Docker Compose deployment for Frigate AI-powered NVR"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: home-automation
  - tech: frigate
related_documents:
  - "[Home Automation README](../README.md)"
  - "[Official Docs](https://docs.frigate.video/)"
---
-->

# Frigate Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Frigate is an AI-powered NVR (Network Video Recorder) that uses object detection to identify people, cars, and other objects in camera streams, with NVIDIA TensorRT acceleration support.

---

## 1. Contents

```
frigate/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 4GB+ VRAM
- NVIDIA Container Toolkit
- IP cameras with RTSP streams

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Create `config/config.yml` (see below)
3. Run `docker compose up -d`
4. Access UI at `http://localhost:5000`

---

## 4. Configuration

Frigate is configured via `config/config.yml`. Minimal example:

```yaml
mqtt:
  enabled: false

detectors:
  tensorrt:
    type: tensorrt

cameras:
  front_door:
    ffmpeg:
      inputs:
        - path: rtsp://user:pass@192.168.1.100:554/stream
          roles:
            - detect
            - record
    detect:
      width: 1280
      height: 720
      fps: 5
```

---

## 5. TensorRT Detector

The RTX 3080 uses TensorRT for high-performance object detection. The `stable-tensorrt` image includes pre-built engines for common YOLO models.

| Detector | Performance |
|----------|-------------|
| TensorRT (RTX 3080) | ~50ms inference |
| OpenVINO (CPU) | ~200ms inference |
| Coral TPU | ~20ms inference |

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./config` | Configuration files |
| `./storage` | Recordings and snapshots |

---

## 7. Home Assistant Integration

Frigate integrates natively with Home Assistant via MQTT:

1. Enable MQTT in Frigate config
2. Install Frigate integration in HA
3. Entities auto-discovered for each camera

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.frigate.video/) | Upstream docs |
| [Frigate GitHub](https://github.com/blakeblackshear/frigate) | Source code |
| [Home Automation](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
