<!--
---
title: "Databases"
description: "Docker Compose recipes for database systems of all types"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
---
-->

# Databases

Docker Compose recipes for database systems organized by data model. This category covers relational databases, NoSQL stores, specialized databases for time series, graphs, and vectors, plus web-based administration tools.

---

## 1. Contents

```
databases/
├── relational/         # SQL databases (MySQL, MariaDB, PostgreSQL, SQLite)
├── document/           # Document stores (MongoDB, CouchDB)
├── key-value/          # Key-value stores (Redis, DragonFly)
├── graph/              # Graph databases (Neo4j)
├── timeseries/         # Time series databases (InfluxDB, QuestDB)
├── vector/             # Vector databases (Qdrant, Milvus, Weaviate, Chroma)
├── wide-column/        # Wide-column stores (Cassandra)
├── management/         # Admin tools (phpMyAdmin, pgAdmin, etc.)
└── README.md           # This file
```

---

## 2. Subcategories

| Directory | Description | Recipe Count |
|-----------|-------------|--------------|
| [relational/](relational/README.md) | SQL databases with ACID transactions | 3 active, 1 planned |
| [document/](document/README.md) | JSON document stores | 2 active |
| [key-value/](key-value/README.md) | In-memory data stores | 1 active, 1 planned |
| [graph/](graph/README.md) | Relationship-focused databases | 1 active |
| [timeseries/](timeseries/README.md) | Time-stamped data optimization | 1 active, 1 planned |
| [vector/](vector/README.md) | Embedding storage for AI/ML | 4 planned |
| [wide-column/](wide-column/README.md) | Distributed columnar storage | 1 active |
| [management/](management/README.md) | Web admin interfaces | 4 planned |

---

## 3. Quick Reference

| Need | Recommended |
|------|-------------|
| General web application | MySQL or PostgreSQL |
| Caching/sessions | Redis |
| Document storage | MongoDB |
| Metrics/monitoring | InfluxDB |
| Knowledge graphs | Neo4j |
| AI embeddings/RAG | Qdrant or Chroma |
| High-scale distributed | Cassandra |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [monitoring-logging/](../monitoring-logging/README.md) | Grafana for visualization |
| [ai-ml/](../ai-ml/README.md) | LLM tools that use vector DBs |
