<!--
---
title: "Database Management Tools"
description: "Web-based administration interfaces for database systems"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: management
---
-->

# Database Management Tools

Web-based administration interfaces for database systems. These tools provide GUI access for database management, query execution, user administration, and monitoring.

---

## 1. Contents

```
management/
├── phpmyadmin/       # phpMyAdmin for MySQL/MariaDB
├── pgadmin/          # pgAdmin for PostgreSQL
├── redis-commander/  # Redis Commander for Redis
├── mongo-express/    # Mongo Express for MongoDB
└── README.md         # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [phpmyadmin/](phpmyadmin/README.md) | phpMyAdmin - MySQL/MariaDB web interface | ✅ Active |
| [pgadmin/](pgadmin/README.md) | pgAdmin - PostgreSQL administration | ✅ Active |
| [redis-commander/](redis-commander/README.md) | Redis Commander - Redis web UI | ✅ Active |
| [mongo-express/](mongo-express/README.md) | Mongo Express - MongoDB web interface | ✅ Active |

---

## 3. Recipe Count: 4

---

## 4. Tool Matrix

| Tool | Database | Key Features |
|------|----------|--------------|
| phpMyAdmin | MySQL, MariaDB | SQL editor, import/export, user management |
| pgAdmin | PostgreSQL | Query tool, schema browser, dashboards |
| Redis Commander | Redis | Key browser, CLI, real-time monitoring |
| Mongo Express | MongoDB | Document viewer, query interface, indexes |

---

## 5. Security Note

These tools provide direct database access. In production:

- Run behind reverse proxy with authentication (Authentik, Authelia)
- Restrict network access to admin networks only
- Use strong, unique credentials
- Consider disabling when not actively needed

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [relational/](../relational/README.md) | MySQL, MariaDB, PostgreSQL |
| [key-value/](../key-value/README.md) | Redis, Dragonfly |
| [document/](../document/README.md) | MongoDB, CouchDB |
| [security/](../../security/README.md) | Authentication (Authentik) |
