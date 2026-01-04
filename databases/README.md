<!--
---
title: "Databases"
description: "SQL, NoSQL, time series, vector, and graph databases"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
---
-->

# Databases

Docker Compose recipes for databases organized by data model: relational, document, key-value, graph, time series, vector, wide-column, and management tools.

---

## 1. Contents

```
databases/
├── relational/     # SQL databases (MySQL, MariaDB, PostgreSQL, SQLite)
├── document/       # Document stores (MongoDB, CouchDB)
├── key-value/      # In-memory stores (Redis, Dragonfly)
├── graph/          # Graph databases (Neo4j)
├── timeseries/     # Time series (InfluxDB, QuestDB)
├── vector/         # Vector embeddings (Qdrant, Milvus, Weaviate, ChromaDB)
├── wide-column/    # Wide-column stores (Cassandra)
├── management/     # Admin tools (pgAdmin, phpMyAdmin, etc.)
└── README.md       # This file
```

---

## 2. Subdirectories

| Directory | Description | Recipes |
|-----------|-------------|---------|
| [relational/](relational/README.md) | Traditional SQL databases | MySQL, MariaDB, PostgreSQL, SQLite |
| [document/](document/README.md) | Schema-flexible document stores | MongoDB, CouchDB |
| [key-value/](key-value/README.md) | High-performance caching | Redis, Dragonfly |
| [graph/](graph/README.md) | Relationship-focused databases | Neo4j |
| [timeseries/](timeseries/README.md) | Time-stamped data optimization | InfluxDB, QuestDB |
| [vector/](vector/README.md) | Embedding storage for AI/RAG | Qdrant, Milvus, Weaviate, ChromaDB |
| [wide-column/](wide-column/README.md) | Distributed wide-column stores | Cassandra |
| [management/](management/README.md) | Database admin interfaces | pgAdmin, phpMyAdmin, Mongo Express, Redis Commander |

---

## 3. Recipe Count

| Subcategory | Count |
|-------------|-------|
| relational | 4 |
| document | 2 |
| key-value | 2 |
| graph | 1 |
| timeseries | 2 |
| vector | 4 |
| wide-column | 1 |
| management | 4 |
| **Total** | **20** |

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| General-purpose SQL | PostgreSQL |
| WordPress/PHP apps | MariaDB or MySQL |
| Lightweight/embedded | SQLite |
| Flexible schema | MongoDB |
| High-speed caching | Redis or Dragonfly |
| Knowledge graphs | Neo4j |
| Metrics/monitoring | InfluxDB or QuestDB |
| AI embeddings/RAG | Qdrant (simple) or Milvus (scale) |
| Distributed writes | Cassandra |

---

## 5. Data Model Selection

| Data Model | Best For | Trade-offs |
|------------|----------|------------|
| Relational | Structured data, ACID transactions | Schema rigidity |
| Document | Variable schemas, rapid development | Less join support |
| Key-Value | Caching, sessions, real-time | Limited querying |
| Graph | Relationships, recommendations | Learning curve |
| Time Series | Metrics, IoT, logs | Specialized queries |
| Vector | Semantic search, RAG | Emerging ecosystem |
| Wide-Column | Write-heavy, distributed | Complexity |

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [ai-ml/](../ai-ml/README.md) | AI workloads using vector DBs |
| [monitoring-logging/](../monitoring-logging/README.md) | Database metrics |
