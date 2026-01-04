<!--
---
title: "Development & CI/CD"
description: "Git servers, CI/CD pipelines, and development tools"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: development-ci-cd
---
-->

# Development & CI/CD

Docker Compose recipes for Git servers, CI/CD pipelines, and development environments.

---

## 1. Contents

```
development-ci-cd/
├── code-server/        # VS Code in the browser
├── gitea-mysql/        # Gitea with MySQL
├── gitea-postgresql/   # Gitea with PostgreSQL
├── gitea-sqlite3/      # Gitea with SQLite
├── gitlabce/           # GitLab Community Edition
├── gogs-mysql/         # Gogs with MySQL
├── gogs-postgres/      # Gogs with PostgreSQL
├── gogs-sqlite3/       # Gogs with SQLite
├── jenkins-sqlite3/    # Jenkins CI
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [code-server](code-server/README.md) | VS Code in the browser | Remote development |
| [gitea-mysql](gitea-mysql/README.md) | Gitea with MySQL backend | Production Git server |
| [gitea-postgresql](gitea-postgresql/README.md) | Gitea with PostgreSQL backend | Production Git server |
| [gitea-sqlite3](gitea-sqlite3/README.md) | Gitea with SQLite backend | Lightweight Git server |
| [gitlabce](gitlabce/README.md) | GitLab Community Edition | Full DevOps platform |
| [gogs-mysql](gogs-mysql/README.md) | Gogs with MySQL backend | Minimal Git server |
| [gogs-postgres](gogs-postgres/README.md) | Gogs with PostgreSQL backend | Minimal Git server |
| [gogs-sqlite3](gogs-sqlite3/README.md) | Gogs with SQLite backend | Minimal Git server |
| [jenkins-sqlite3](jenkins-sqlite3/README.md) | Jenkins CI server | Build automation |

---

## 3. Recipe Count: 9

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Lightweight Git server | Gitea (SQLite) or Gogs |
| Production Git server | Gitea (PostgreSQL) |
| Full DevOps platform | GitLab CE |
| CI/CD pipelines | Jenkins or GitLab CI |
| Remote development | Code-Server |

---

## 5. Git Server Comparison

| Feature | Gitea | Gogs | GitLab CE |
|---------|-------|------|-----------|
| Resource usage | Low | Very Low | High |
| Built-in CI/CD | Actions (beta) | ❌ | ✅ Full |
| Container registry | ✅ | ❌ | ✅ |
| Issue tracking | ✅ | ✅ | ✅ |
| Wiki | ✅ | ✅ | ✅ |
| Learning curve | Low | Low | Medium |

---

## 6. Database Backend Selection

| Backend | Best For |
|---------|----------|
| SQLite | Single user, low traffic, testing |
| MySQL/MariaDB | Existing MySQL infrastructure |
| PostgreSQL | Production, advanced features |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [container-management/](../container-management/README.md) | Container orchestration |
| [automation-orchestration/](../automation-orchestration/README.md) | Workflow automation |
