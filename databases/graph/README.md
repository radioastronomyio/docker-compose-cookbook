<!--
---
title: "Graph Databases"
description: "Databases optimized for storing and querying connected data"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: graph
---
-->

# Graph Databases

Databases designed for storing and querying highly connected data. Graph databases excel at relationship-heavy queries, social networks, recommendation engines, and knowledge graphs.

---

## 1. Contents

```
graph/
├── neo4j/        # Neo4j graph database
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [neo4j/](neo4j/README.md) | Neo4j - native graph database with Cypher query language | ✅ Active |

---

## 3. Recipe Count: 1

---

## 4. Use Cases

| Use Case | Why Graph? |
|----------|------------|
| Social networks | Friend-of-friend queries in milliseconds |
| Fraud detection | Pattern matching across transactions |
| Recommendations | Collaborative filtering via relationships |
| Knowledge graphs | Semantic relationships and inference |
| Network analysis | Infrastructure dependencies, impact analysis |

---

## 5. Query Language

Neo4j uses Cypher, a declarative graph query language:

```cypher
MATCH (user:Person)-[:FRIENDS_WITH]->(friend)-[:LIKES]->(movie:Movie)
WHERE user.name = 'Alice'
RETURN movie.title, count(friend) as recommendations
ORDER BY recommendations DESC
```

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [ai-ml/](../../ai-ml/README.md) | Knowledge graph applications |
