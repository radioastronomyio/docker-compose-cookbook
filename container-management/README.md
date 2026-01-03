<!--
---
title: "Container Management"
description: "Container orchestration and management interfaces"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: container-management
---
-->

# Container Management

Docker Compose recipes for container orchestration, management UIs, and container lifecycle tools.

---

## 1. Contents

```
container-management/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| portainer | Container management UI | High |
| dockge | Docker Compose stack manager | High |
| yacht | Simple container management | Medium |
| watchtower | Automatic container updates | Medium |
| diun | Docker image update notifier | Low |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Full management UI | Portainer |
| Compose-focused management | Dockge |
| Simple web UI | Yacht |
| Auto-update containers | Watchtower |
| Update notifications only | Diun |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [development-ci-cd/](../development-ci-cd/README.md) | CI/CD for container builds |
| [monitoring-logging/](../monitoring-logging/README.md) | Container metrics |
