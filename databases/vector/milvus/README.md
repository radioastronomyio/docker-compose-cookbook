<!--
---
title: "Milvus"
description: "Enterprise-scale vector database with robust GPU acceleration"
author: "VintageDon"
tags:
  - type: recipe
  - category: databases/vector
  - application: milvus
---
-->

# Milvus

Enterprise-grade vector database designed for massive scale, offering the most robust GPU support among vector databases with algorithms like IVF_FLAT and IVF_SQ8 optimized for NVIDIA hardware.

---

## 1. Overview

Milvus is designed for billion-scale vector search. The GPU version provides the lowest search latency for large datasets. Requires Etcd for metadata coordination and MinIO for object storage.

| Attribute | Value |
|-----------|-------|
| **Image** | `milvusdb/milvus:v2.3.4-gpu` |
| **Ports** | 19530 (gRPC API) |
| **GPU Required** | Yes (for GPU image) |
| **Documentation** | [milvus.io/docs](https://milvus.io/docs/) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| NVIDIA GPU | 4GB+ VRAM |
| Memory | 8GB+ RAM for standalone |

---

## 3. Quick Start

```bash
# Clone and navigate
cd databases/vector/milvus

# Start the stack (includes etcd and minio)
docker compose up -d

# Wait for initialization (~30 seconds)
# Connect via SDK on port 19530
```

---

## 4. Architecture

Milvus standalone bundles coordinator and worker nodes but requires:

| Service | Purpose |
|---------|---------|
| **etcd** | Metadata storage and coordination |
| **minio** | Object storage for vector data |
| **milvus** | Core vector engine |

---

## 5. Configuration

### 5.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `ETCD_ENDPOINTS` | `etcd:2379` | Etcd connection |
| `MINIO_ADDRESS` | `minio:9000` | MinIO connection |

### 5.2 MinIO Credentials

Default credentials (change in production):

- Access Key: `minioadmin`
- Secret Key: `minioadmin`

---

## 6. GPU Index Types

| Index | Use Case |
|-------|----------|
| `IVF_FLAT` | High accuracy, moderate speed |
| `IVF_SQ8` | Balanced accuracy/speed, lower memory |
| `IVF_PQ` | Lowest memory, some accuracy trade-off |

---

## 7. Python Client

```python
from pymilvus import connections, Collection

connections.connect(host="localhost", port="19530")

collection = Collection("my_vectors")
```

---

## 8. Volumes

| Volume | Purpose |
|--------|---------|
| `milvus_data` | Vector storage and indexes |
| `etcd_data` | Metadata (implicit in etcd) |
| `minio_data` | Object storage (implicit in minio) |

---

## 9. Resource Requirements

| Scale | RAM | GPU VRAM |
|-------|-----|----------|
| <1M vectors | 8GB | 4GB |
| 1-10M vectors | 16GB | 8GB |
| 10-100M vectors | 32GB+ | 12GB+ |

---

## 10. Related

| Document | Relationship |
|----------|--------------|
| [Vector Databases README](../README.md) | Parent category |
| [Qdrant](../qdrant/README.md) | Simpler alternative |
| [Weaviate](../weaviate/README.md) | Module-based alternative |
