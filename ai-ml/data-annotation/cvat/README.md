<!--
---
title: "CVAT Docker Setup"
description: "Docker Compose deployment for CVAT computer vision annotation"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: data-annotation
  - tech: cvat
related_documents:
  - "[Data Annotation README](../README.md)"
  - "[Official Docs](https://docs.cvat.ai/)"
---
-->

# CVAT Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

CVAT (Computer Vision Annotation Tool) is a specialized annotation platform for image and video data. It excels at video interpolation, 3D point cloud annotation, and large-scale segmentation tasks that generic tools struggle with.

---

## 1. Contents

```
cvat/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Machine's IP address (not localhost)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Set `CVAT_HOST` to your machine's IP address (e.g., `192.168.1.50`)
3. Set a secure `CVAT_POSTGRES_PASSWORD`
4. Run `docker compose up -d`
5. Wait for all services to stabilize (~60 seconds)
6. Create superuser (see below)
7. Access UI at `http://<CVAT_HOST>:8090`

### Create Superuser

CVAT does not support initial admin creation via environment variables. Run manually:

```bash
docker exec -it cvat_server bash -ic 'python3 ~/manage.py createsuperuser'
```

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `CVAT_PORT` | 8090 | Web UI port |
| `CVAT_HOST` | - | Machine IP/FQDN (required, NOT localhost) |
| `CVAT_POSTGRES_PASSWORD` | - | Database password (required) |

### Critical: CVAT_HOST

The `CVAT_HOST` variable must be set to your machine's IP or fully qualified domain name **before startup**. Using `localhost` breaks the UI when accessed from other machines due to Traefik's internal routing rules.

---

## 5. Architecture

CVAT uses a microservices architecture:

| Service | Purpose |
|---------|---------|
| `cvat_server` | Django backend, API, task processing |
| `cvat_ui` | React frontend |
| `cvat_db` | PostgreSQL for annotations/metadata |
| `cvat_redis` | Task queue and caching |
| `traefik` | Reverse proxy and internal routing |

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `cvat_db` | PostgreSQL database |
| `cvat_data` | Uploaded images, videos, task data |
| `cvat_keys` | Security keys |
| `cvat_logs` | Application logs |

---

## 7. Annotation Features

| Feature | Description |
|---------|-------------|
| Video Interpolation | Annotate keyframes, CVAT interpolates between |
| 3D Point Clouds | LiDAR and depth sensor annotation |
| Automatic Annotation | AI-assisted labeling with serverless functions |
| Track Mode | Object tracking across video frames |
| Attribute Annotation | Additional metadata per object |

---

## 8. Export Formats

- COCO 1.0
- CVAT for images/video
- Datumaro
- LabelMe 3.0
- MOT (Multiple Object Tracking)
- Pascal VOC
- YOLO

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.cvat.ai/) | Upstream docs |
| [GitHub Repository](https://github.com/opencv/cvat) | Source code |
| [Data Annotation](../README.md) | Parent category |
| [Label Studio](../label-studio/README.md) | Alternative for multi-modal data |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
