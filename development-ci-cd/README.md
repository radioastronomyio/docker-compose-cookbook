<!--
---
title: "Development & CI/CD"
description: "Git servers, continuous integration, and development tools"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: development-ci-cd
---
-->

# Development & CI/CD

Docker Compose recipes for self-hosted Git servers, continuous integration pipelines, and development tools.

---

## 1. Contents

```
development-ci-cd/
├── gitea-mysql/            # Gitea with MySQL
├── gitea-postgresql/       # Gitea with PostgreSQL
├── gitea-sqlite3/          # Gitea with SQLite
├── gitlabce/               # GitLab Community Edition
├── gogs-mysql/             # Gogs with MySQL
├── gogs-postgres/          # Gogs with PostgreSQL
├── gogs-sqlite3/           # Gogs with SQLite
├── jenkins-sqlite3/        # Jenkins CI server
└── README.md               # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [gitea-mysql/](gitea-mysql/README.md) | Gitea with MySQL backend | ✅ Active |
| [gitea-postgresql/](gitea-postgresql/README.md) | Gitea with PostgreSQL backend | ✅ Active |
| [gitea-sqlite3/](gitea-sqlite3/README.md) | Gitea with SQLite (lightweight) | ✅ Active |
| [gitlabce/](gitlabce/README.md) | GitLab CE - full DevOps platform | ✅ Active |
| [gogs-mysql/](gogs-mysql/README.md) | Gogs with MySQL backend | ✅ Active |
| [gogs-postgres/](gogs-postgres/README.md) | Gogs with PostgreSQL backend | ✅ Active |
| [gogs-sqlite3/](gogs-sqlite3/README.md) | Gogs with SQLite (minimal) | ✅ Active |
| [jenkins-sqlite3/](jenkins-sqlite3/README.md) | Jenkins automation server | ✅ Active |

---

## 3. Comparison

| Tool | Resources | Features | Best For |
|------|-----------|----------|----------|
| Gogs | Minimal | Git hosting | Simple, low-resource environments |
| Gitea | Low | Git + issues + wiki | Small teams, Gogs replacement |
| GitLab CE | High | Full DevOps suite | Enterprise, all-in-one platform |
| Jenkins | Medium | CI/CD pipelines | Complex build automation |

---

## 4. Database Variants

Most Git servers support multiple databases. Choose based on your needs:

| Database | Use Case |
|----------|----------|
| SQLite | Development, single-user, low-traffic |
| MySQL/MariaDB | Production with existing MySQL infrastructure |
| PostgreSQL | Production with advanced query needs |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [automation-orchestration/](../automation-orchestration/README.md) | Infrastructure automation |
| [container-management/](../container-management/README.md) | Container deployment tools |
