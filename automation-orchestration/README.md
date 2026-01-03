<!--
---
title: "Automation & Orchestration"
description: "Infrastructure automation, configuration management, and runbook tools"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: automation-orchestration
---
-->

# Automation & Orchestration

Docker Compose recipes for infrastructure automation, configuration management, and runbook execution. These tools help automate repetitive tasks and manage infrastructure at scale.

---

## 1. Contents

```
automation-orchestration/
├── ansibleawx-postgres-redis/              # AWX (Ansible Tower)
├── rundeck/                                # Job scheduler
├── stackstorm-mongodb-rabbitmq-postgres/   # Event-driven automation
└── README.md                               # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [ansibleawx-postgres-redis/](ansibleawx-postgres-redis/README.md) | AWX - web UI for Ansible automation | ✅ Active |
| [rundeck/](rundeck/README.md) | Rundeck - runbook automation and job scheduling | ✅ Active |
| [stackstorm-mongodb-rabbitmq-postgres/](stackstorm-mongodb-rabbitmq-postgres/README.md) | StackStorm - event-driven automation | ✅ Active |

---

## 3. Use Cases

| Tool | Best For |
|------|----------|
| AWX | Ansible playbook management, credential storage, scheduling |
| Rundeck | Self-service operations, scheduled jobs, runbooks |
| StackStorm | Event-driven automation, ChatOps, remediation workflows |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [data-pipelines/](../data-pipelines/README.md) | Workflow orchestration (Airflow, etc.) |
| [development-ci-cd/](../development-ci-cd/README.md) | CI/CD pipelines |
