<!--
---
title: "Relational Databases"
description: "SQL-based relational database management systems"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
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
├── mysql/              # MySQL Server
├── mariadb/            # MariaDB (MySQL fork)
├── sqlite3/            # SQLite embedded database
├── postgresql/         # PostgreSQL (planned)
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [mysql/](mysql/README.md) | MySQL Server - widely used open-source RDBMS | ✅ Active |
| [mariadb/](mariadb/README.md) | MariaDB - community-developed MySQL fork | ✅ Active |
| [sqlite3/](sqlite3/README.md) | SQLite - lightweight serverless database | ✅ Active |
| [postgresql/](postgresql/) | PostgreSQL - advanced open-source RDBMS | 📋 Planned |

---

## 3. Use Cases

| Database | Best For |
|----------|----------|
| MySQL | Web applications, WordPress, general purpose |
| MariaDB | MySQL replacement with enhanced features |
| SQLite | Embedded applications, development, testing |
| PostgreSQL | Complex queries, PostGIS, pgvector, enterprise |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [management/](../management/README.md) | Admin tools (phpMyAdmin, pgAdmin) |
