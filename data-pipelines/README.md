<!--
---
title: "Data Pipelines"
description: "Workflow orchestration, ETL, and data processing tools"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: data-pipelines
---
-->

# Data Pipelines

Docker Compose recipes for workflow orchestration, ETL pipelines, and data processing tools.

---

## 1. Contents

```
data-pipelines/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| airflow | Workflow orchestration | High |
| n8n | Workflow automation (low-code) | High |
| dagster | Data orchestration platform | Medium |
| prefect | Modern workflow orchestration | Medium |
| nifi | Data flow automation | Medium |
| airbyte | Data integration (ELT) | Medium |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Complex DAG workflows | Airflow |
| Visual workflow builder | n8n |
| Data-aware orchestration | Dagster |
| Modern Python workflows | Prefect |
| Data integration/ELT | Airbyte |

---

## 4. Comparison

| Tool | Approach | Best For |
|------|----------|----------|
| Airflow | Python DAGs | Complex scheduling, ML pipelines |
| n8n | Visual nodes | Integrations, automations |
| Dagster | Software-defined assets | Data engineering |
| Prefect | Python-native | Dynamic workflows |

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [automation-orchestration/](../automation-orchestration/README.md) | Infrastructure automation |
| [databases/](../databases/README.md) | Data storage backends |
| [ai-ml/](../ai-ml/README.md) | ML model training pipelines |
