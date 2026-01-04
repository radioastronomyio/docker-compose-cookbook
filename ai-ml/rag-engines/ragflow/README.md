<!--
---
title: "RAGFlow Docker Setup"
description: "Docker Compose deployment for RAGFlow deep document understanding RAG"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: rag-engines
  - tech: ragflow
related_documents:
  - "[RAG Engines README](../README.md)"
  - "[Official Docs](https://ragflow.io/docs)"
---
-->

# RAGFlow Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

RAGFlow is a deep document understanding RAG engine that uses vision-based layout analysis to interpret complex PDFs, charts, and tables before vectorization. Unlike generic RAG systems that chunk text blindly, RAGFlow preserves document structure semantics.

---

## 1. Contents

```
ragflow/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 8GB+ VRAM
- NVIDIA Container Toolkit
- **WSL2**: `vm.max_map_count >= 262144` (see .env.example)

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and set secure passwords
2. Configure WSL2 kernel parameters (see .env.example)
3. Run `docker compose up -d`
4. Wait for all health checks to pass (~2-3 minutes)
5. Access UI at `http://localhost:9380`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `MYSQL_PASSWORD` | - | MySQL root password (required) |
| `MINIO_PASSWORD` | - | MinIO admin password (required) |
| `REDIS_PASSWORD` | - | Redis auth password (required) |
| `ES_HEAP` | 512m | Elasticsearch heap size |
| `TZ` | America/New_York | Container timezone |

### Critical Setup Notes

**Elasticsearch Kernel Tuning**: RAGFlow uses Elasticsearch which requires increased virtual memory limits. Without this, Elasticsearch crashes silently.

For WSL2, add to `%USERPROFILE%\.wslconfig`:

```ini
[wsl2]
kernelCommandLine = "sysctl.vm.max_map_count=262144"
```

Then restart WSL: `wsl --shutdown`

---

## 5. Architecture

RAGFlow bundles five services:

| Service | Purpose |
|---------|---------|
| `ragflow` | Main application with GPU-accelerated OCR |
| `es01` | Elasticsearch for hybrid keyword/vector search |
| `mysql` | Metadata and configuration storage |
| `minio` | S3-compatible object storage for documents |
| `redis` | Caching and session management |

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `esdata01` | Elasticsearch indices |
| `mysql_data` | Database files |
| `minio_data` | Uploaded documents |
| `redis_data` | Cache persistence |
| `ragflow-logs` | Application logs |

---

## 7. GPU Acceleration

The OCR components (DeepDoc) benefit significantly from GPU acceleration. Document ingestion time drops from minutes to seconds for large libraries.

The compose file reserves one NVIDIA GPU for the ragflow container.

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://ragflow.io/docs) | Upstream docs |
| [GitHub Repository](https://github.com/infiniflow/ragflow) | Source code |
| [RAG Engines](../README.md) | Parent category |
| [Vector Databases](../../../databases/vector/README.md) | Alternative embedding storage |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
