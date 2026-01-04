<!--
---
title: "Relational Databases"
description: "SQL-based relational database management systems"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: relational
---
-->

# Relational Databases

SQL-based relational database management systems. These databases use structured schemas with tables, rows, and columns, supporting ACID transactions and complex queries via SQL.

---

## 1. Contents

```
relational/
├── mysql/        # MySQL Server
├── mariadb/      # MariaDB (MySQL fork)
├── postgresql/   # PostgreSQL
├── sqlite3/      # SQLite embedded database
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [mysql/](mysql/README.md) | MySQL Server - widely used open-source RDBMS | ✅ Active |
| [mariadb/](mariadb/README.md) | MariaDB - community-developed MySQL fork | ✅ Active |
| [postgresql/](postgresql/README.md) | PostgreSQL - advanced open-source RDBMS | ✅ Active |
| [sqlite3/](sqlite3/README.md) | SQLite - lightweight serverless database | ✅ Active |

---

## 3. Recipe Count: 4

---

## 4. Selection Guide

| Database | Best For |
|----------|----------|
| MySQL | Web applications, WordPress, general purpose |
| MariaDB | MySQL replacement with enhanced features |
| PostgreSQL | Complex queries, PostGIS, pgvector, enterprise |
| SQLite | Embedded applications, development, testing |

---

## 5. Comparison

| Feature | MySQL | MariaDB | PostgreSQL | SQLite |
|---------|-------|---------|------------|--------|
| Concurrency | Good | Good | Excellent | Limited |
| JSON support | ✅ | ✅ | ✅ Native | ✅ |
| Full-text search | ✅ | ✅ | ✅ | Extension |
| Spatial (GIS) | ✅ | ✅ | PostGIS | ❌ |
| Resource usage | Medium | Medium | Medium | Minimal |

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [management/](../management/README.md) | Admin tools (phpMyAdmin, pgAdmin) |
