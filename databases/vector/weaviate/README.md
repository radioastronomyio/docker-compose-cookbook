<!--
---
title: "Weaviate Docker Setup"
description: "Docker Compose deployment for Weaviate vector database with GPU-accelerated embeddings"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: databases
  - subcategory: vector
  - tech: weaviate
related_documents:
  - "[Vector Databases README](../README.md)"
  - "[Official Docs](https://weaviate.io/developers/weaviate)"
---
-->

# Weaviate Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Weaviate is a modular AI-native vector database that can handle vectorization internally via modules, rather than relying on external embedding services.

---

## 1. Contents

```
weaviate/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- NVIDIA GPU with 4GB+ VRAM (for embedding module)
- NVIDIA Container Toolkit

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access API at `http://localhost:8080`
4. Access gRPC at `localhost:50051`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `QUERY_DEFAULTS_LIMIT` | 25 | Default query result limit |
| `AUTHENTICATION_ANONYMOUS_ACCESS_ENABLED` | true | Allow anonymous access |
| `DEFAULT_VECTORIZER_MODULE` | text2vec-transformers | Default embedding module |
| `ENABLE_CUDA` | 1 | GPU acceleration for embeddings |

### Architecture Notes

This setup uses the `text2vec-transformers` module as a GPU-accelerated sidecar container. The RTX 3080 handles embedding generation while Weaviate manages storage and retrieval.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `weaviate_data` | Vector indices and metadata |

---

## 6. API Usage

```bash
# Check readiness
curl http://localhost:8080/v1/.well-known/ready

# Get schema
curl http://localhost:8080/v1/schema

# Create a class
curl -X POST http://localhost:8080/v1/schema -H "Content-Type: application/json" -d '{
  "class": "Document",
  "vectorizer": "text2vec-transformers"
}'
```

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://weaviate.io/developers/weaviate) | Upstream docs |
| [Weaviate Console](https://console.weaviate.cloud/) | Web-based management |
| [Vector Databases](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
