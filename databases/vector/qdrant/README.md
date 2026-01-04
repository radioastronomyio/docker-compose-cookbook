<!--
---
title: "Qdrant"
description: "High-performance Rust-based vector database with GPU-accelerated indexing"
author: "VintageDon"
tags:
  - type: recipe
  - category: databases/vector
  - application: qdrant
---
-->

# Qdrant

Production-grade vector database written in Rust, known for exceptional performance, ease of use via REST API, and optional GPU-accelerated indexing for faster ingestion.

---

## 1. Overview

Qdrant excels at similarity search with features like filtering, payload storage, and distributed deployment. One of the few vector databases with explicit GPU support for accelerating HNSW index construction.

| Attribute | Value |
|-----------|-------|
| **Image** | `qdrant/qdrant:latest` |
| **Ports** | 6333 (REST API), 6334 (gRPC) |
| **GPU Required** | Optional (for accelerated indexing) |
| **Documentation** | [qdrant.tech/documentation](https://qdrant.tech/documentation/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | Optional, for index acceleration |

---

## 3. Quick Start

```bash
# Clone and navigate
cd databases/vector/qdrant

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access dashboard
open http://localhost:6333/dashboard
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `QDRANT__GPU__INDEXING` | `true` | Enable GPU-accelerated indexing |
| `QDRANT__SERVICE__API_KEY` | (optional) | API key for authentication |

---

## 5. GPU Acceleration

With `QDRANT__GPU__INDEXING=true`, the RTX 3080 performs distance calculations during HNSW graph construction significantly faster than CPU. Benefits are most noticeable when:

- Ingesting millions of vectors
- Re-indexing collections
- Building indexes with high `ef_construct` values

Remove the `deploy` section to run CPU-only.

---

## 6. API Usage

### 6.1 Create Collection

```bash
curl -X PUT http://localhost:6333/collections/my_collection \
  -H "Content-Type: application/json" \
  -d '{
    "vectors": {
      "size": 384,
      "distance": "Cosine"
    }
  }'
```

### 6.2 Python Client

```python
from qdrant_client import QdrantClient

client = QdrantClient(host="localhost", port=6333)
```

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./qdrant_storage` | Vector data, indexes, snapshots |

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Vector Databases README](../README.md) | Parent category |
| [Milvus](../milvus/README.md) | Enterprise alternative |
| [RAG Chat Interfaces](../../../ai-ml/chat-interfaces/README.md) | Common use case |
