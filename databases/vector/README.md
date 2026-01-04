<!--
---
title: "Vector Databases"
description: "Databases optimized for storing and searching vector embeddings"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
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
├── qdrant/       # Qdrant vector search
├── milvus/       # Milvus scalable vectors
├── weaviate/     # Weaviate ML-first search
├── chroma/       # ChromaDB embedding store
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [qdrant/](qdrant/README.md) | Qdrant - Rust-based vector similarity engine | ✅ Active |
| [milvus/](milvus/README.md) | Milvus - scalable vector database | ✅ Active |
| [weaviate/](weaviate/README.md) | Weaviate - ML-first vector search | ✅ Active |
| [chroma/](chroma/README.md) | ChromaDB - AI-native embedding database | ✅ Active |

---

## 3. Recipe Count: 4

---

## 4. Selection Guide

| Database | Best For |
|----------|----------|
| Qdrant | Production RAG, high-performance similarity search |
| Milvus | Large-scale vector search, enterprise deployments |
| Weaviate | Semantic search with built-in ML models |
| ChromaDB | Local development, LangChain integration, lightweight RAG |

---

## 5. Comparison

| Feature | Qdrant | Milvus | Weaviate | ChromaDB |
|---------|--------|--------|----------|----------|
| Language | Rust | Go/C++ | Go | Python |
| Filtering | ✅ Rich | ✅ Rich | ✅ GraphQL | ✅ Basic |
| Persistence | ✅ | ✅ | ✅ | ✅ |
| Clustering | ✅ | ✅ | ✅ | ❌ |
| Resource usage | Low | High | Medium | Low |
| Best for | Production | Scale | ML-native | Development |

---

## 6. RAG Architecture

Vector databases are the retrieval layer in RAG systems:

```
Documents → Embedding Model → Vector DB
                                  ↓
Query → Embedding Model → Similarity Search → Context → LLM → Response
```

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [ai-ml/llm-inference/](../../ai-ml/llm-inference/README.md) | LLM backends |
| [ai-ml/chat-interfaces/](../../ai-ml/chat-interfaces/README.md) | RAG-capable UIs |
| [ai-ml/rag-engines/](../../ai-ml/rag-engines/README.md) | Full RAG platforms |
