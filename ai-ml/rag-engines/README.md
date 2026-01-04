<!--
---
title: "RAG Engines"
description: "Docker recipes for Retrieval-Augmented Generation systems"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: rag-engines
---
-->

# RAG Engines

Docker Compose recipes for Retrieval-Augmented Generation (RAG) systems. These platforms combine document ingestion, vector search, and LLM synthesis to answer questions from proprietary knowledge bases.

---

## 1. Contents

```
rag-engines/
├── ragflow/                   # Deep document understanding RAG
└── README.md                  # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [ragflow/](ragflow/README.md) | Vision-based document parsing with hybrid search | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Complex PDFs, tables, charts | RAGFlow |
| Simple text documents | Consider PrivateGPT in chat-interfaces |

---

## 4. Architecture Notes

RAG engines typically require:

- **Vector Database**: Stores document embeddings (see [databases/vector](../../databases/vector/README.md))
- **LLM Backend**: Generates responses (see [llm-inference](../llm-inference/README.md))
- **Object Storage**: Stores original documents (MinIO, S3-compatible)

RAGFlow bundles these dependencies internally for a simpler deployment.

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [Vector Databases](../../databases/vector/README.md) | Embedding storage |
| [LLM Inference](../llm-inference/README.md) | Generation backends |
| [Chat Interfaces](../chat-interfaces/README.md) | Alternative RAG-capable UIs |
