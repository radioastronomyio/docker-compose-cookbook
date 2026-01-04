<!--
---
title: "Automation & Orchestration"
description: "Workflow engines, infrastructure automation, and AI agent platforms"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: automation-orchestration
---
-->

# Automation & Orchestration

Docker Compose recipes for infrastructure automation, workflow engines, AI agent platforms, and scheduled task management.

---

## 1. Contents

```
automation-orchestration/
├── ansibleawx-postgres-redis/           # Ansible AWX
├── changedetection/                     # Website change monitoring
├── dify/                                # GenAI app platform
├── flowise/                             # Low-code LangChain builder
├── n8n/                                 # Workflow automation
├── postiz/                              # Social media scheduling
├── rundeck/                             # Job scheduler
├── stackstorm-mongodb-rabbitmq-postgres/ # Event-driven automation
└── README.md                            # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [ansibleawx-postgres-redis](ansibleawx-postgres-redis/README.md) | Ansible AWX with PostgreSQL and Redis | Infrastructure as Code UI |
| [rundeck](rundeck/README.md) | Job scheduler and runbook automation | Scheduled operations |
| [stackstorm-mongodb-rabbitmq-postgres](stackstorm-mongodb-rabbitmq-postgres/README.md) | Event-driven automation platform | Complex event processing |
| [n8n](n8n/README.md) | Workflow automation with 400+ integrations | General automation |
| [flowise](flowise/README.md) | Low-code LangChain app builder | AI workflow prototyping |
| [dify](dify/README.md) | GenAI application development platform | Production AI apps |
| [changedetection](changedetection/README.md) | Website change monitoring | Price tracking, content alerts |
| [postiz](postiz/README.md) | Social media scheduling and management | Content automation |

---

## 3. Recipe Count: 8

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Infrastructure automation | Ansible AWX |
| Scheduled jobs/runbooks | Rundeck |
| Event-driven automation | StackStorm |
| General workflow automation | n8n |
| AI/LLM workflows (visual) | Flowise |
| Production AI applications | Dify |
| Website monitoring | ChangeDetection |
| Social media management | Postiz |

---

## 5. Integration Patterns

### AI Workflow Stack

```
n8n/Flowise → Ollama/LocalAI → Vector DB → Output
```

### Infrastructure Automation

```
StackStorm (events) → Ansible AWX (execution) → Rundeck (scheduling)
```

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [ai-ml/](../ai-ml/README.md) | LLM backends for AI workflows |
| [databases/](../databases/README.md) | Data storage for workflows |
| [monitoring-logging/](../monitoring-logging/README.md) | Workflow observability |
