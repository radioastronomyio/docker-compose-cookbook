<!--
---
title: "ChromaDB Docker Setup"
description: "Docker Compose deployment for ChromaDB vector database"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: databases
  - subcategory: vector
  - tech: chromadb
related_documents:
  - "[Vector Databases README](../README.md)"
  - "[Official Docs](https://docs.trychroma.com/)"
---
-->

# ChromaDB Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

ChromaDB is a lightweight, developer-friendly vector database widely used in the LangChain ecosystem. It uses an embedded SQLite/DuckDB backend and is optimized for simplicity.

---

## 1. Contents

```
chroma/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+

Note: ChromaDB is CPU-optimized and does not require GPU acceleration.

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access API at `http://localhost:8000`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `IS_PERSISTENT` | TRUE | Enable persistent storage |
| `ALLOW_RESET` | TRUE | Allow database reset via API (dev only) |
| `ANONYMIZED_TELEMETRY` | FALSE | Disable telemetry |
| `CHROMA_SERVER_AUTH_CREDENTIALS` | - | Optional authentication |

### Development vs Production

- **ALLOW_RESET=TRUE**: Essential for development—allows programmatic database wipes when iterating on RAG pipelines.
- **ALLOW_RESET=FALSE**: Required for production to prevent accidental data loss.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./chroma_data` | Vector indices and collections |

---

## 6. API Usage

```bash
# Health check
curl http://localhost:8000/api/v1/heartbeat

# List collections
curl http://localhost:8000/api/v1/collections

# Create collection
curl -X POST http://localhost:8000/api/v1/collections -H "Content-Type: application/json" -d '{
  "name": "my_collection"
}'
```

---

## 7. Python Client

```python
import chromadb

client = chromadb.HttpClient(host="localhost", port=8000)
collection = client.create_collection("documents")

collection.add(
    documents=["This is a document"],
    ids=["doc1"]
)

results = collection.query(query_texts=["search query"], n_results=5)
```

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.trychroma.com/) | Upstream docs |
| [Chroma Cookbook](https://cookbook.chromadb.dev/) | Usage examples |
| [Vector Databases](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
