<!--
---
title: "Label Studio Docker Setup"
description: "Docker Compose deployment for Label Studio data annotation platform"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: data-annotation
  - tech: label-studio
related_documents:
  - "[Data Annotation README](../README.md)"
  - "[Official Docs](https://labelstud.io/guide/)"
---
-->

# Label Studio Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Label Studio is a universal data annotation platform supporting text, images, audio, video, and time series data. It serves as the upstream dependency for RLHF workflows and custom model training pipelines.

---

## 1. Contents

```
label-studio/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and set a secure password
2. Run `docker compose up -d`
3. Wait for database initialization (~30 seconds)
4. Access UI at `http://localhost:8080`
5. Create your first account (first user becomes admin)

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `LABEL_STUDIO_PORT` | 8080 | Web UI port |
| `PG_PASSWORD` | - | PostgreSQL password (required) |
| `LABEL_STUDIO_HOST` | http://localhost:8080 | External URL for ML callbacks |
| `SSRF_PROTECTION` | true | Block internal network requests |

### SSRF Protection

Label Studio protects against Server-Side Request Forgery by default. If your data resides on internal S3/MinIO buckets, you may need to:

- Set `SSRF_PROTECTION=false`, or
- Whitelist specific internal IPs in Label Studio settings

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `label-studio` | Web application and annotation UI |
| `db` | PostgreSQL for project/annotation storage |

For production with thousands of annotations, this PostgreSQL backend significantly outperforms the default SQLite.

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `labelstudio_data` | Uploaded files, exports, user data |
| `postgres_data` | Database files |

---

## 7. ML Backend Integration

Label Studio can connect to ML backends for pre-labeling (model-assisted annotation):

1. Deploy an ML backend (see [Label Studio ML](https://github.com/HumanSignal/label-studio-ml-backend))
2. Set `LABEL_STUDIO_HOST` to your externally accessible URL
3. Add the ML backend in Project Settings → Machine Learning

The ML backend calls Label Studio's API to fetch tasks and submit predictions.

---

## 8. Supported Data Types

| Type | Annotation Tasks |
|------|-----------------|
| Text | Classification, NER, sentiment, relations |
| Images | Bounding boxes, polygons, keypoints, segmentation |
| Audio | Transcription, classification, speaker diarization |
| Video | Object tracking, action recognition |
| Time Series | Anomaly detection, event labeling |

---

## 9. Export Formats

Label Studio exports to standard ML formats:

- COCO (object detection)
- YOLO (object detection)
- Pascal VOC (object detection)
- CoNLL (NER)
- JSON (universal)
- CSV (tabular)

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://labelstud.io/guide/) | Upstream docs |
| [ML Backend Templates](https://github.com/HumanSignal/label-studio-ml-backend) | Pre-labeling examples |
| [Data Annotation](../README.md) | Parent category |
| [CVAT](../cvat/README.md) | Alternative for computer vision |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
