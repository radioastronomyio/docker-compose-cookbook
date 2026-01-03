<!--
---
title: "Vector Databases"
description: "Databases optimized for storing and searching vector embeddings"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: vector
---
-->

# Vector Databases

Databases designed for storing, indexing, and searching high-dimensional vector embeddings. Essential for AI/ML applications including semantic search, RAG (Retrieval Augmented Generation), recommendation systems, and similarity matching.

---

## 1. Contents

```
vector/
├── qdrant/             # Qdrant (planned)
├── milvus/             # Milvus (planned)
├── weaviate/           # Weaviate (planned)
├── chroma/             # Chroma (planned)
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [qdrant/](qdrant/) | Qdrant - Rust-based vector similarity engine | 📋 Planned |
| [milvus/](milvus/) | Milvus - scalable vector database | 📋 Planned |
| [weaviate/](weaviate/) | Weaviate - ML-first vector search | 📋 Planned |
| [chroma/](chroma/) | Chroma - AI-native embedding database | 📋 Planned |

---

## 3. Use Cases

| Database | Best For |
|----------|----------|
| Qdrant | Production RAG, high-performance similarity search |
| Milvus | Large-scale vector search, enterprise deployments |
| Weaviate | Semantic search with built-in ML models |
| Chroma | Local development, LangChain integration, lightweight RAG |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [ai-ml/](../../ai-ml/README.md) | LLM inference servers (Ollama, etc.) |
