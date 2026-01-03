<!--
---
title: "Dify Docker Setup"
description: "Docker Compose deployment for Dify GenAI development platform"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: automation-orchestration
  - tech: dify
related_documents:
  - "[Automation & Orchestration README](../README.md)"
  - "[Official Docs](https://docs.dify.ai/)"
---
-->

# Dify Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Dify is an enterprise-grade GenAI development platform that provides a structured, application-centric approach to building AI applications with RAG, agents, and workflows.

---

## 1. Contents

```
dify/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- 4GB+ RAM available for containers
- Ollama or other LLM backend

---

## 3. Quick Start

1. Copy `.env.example` to `.env` and adjust variables
2. Run `docker compose up -d`
3. Access Web UI at `http://localhost:3000`
4. Access API at `http://localhost:5001`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `SECRET_KEY` | - | Application secret (generate random) |
| `DB_USERNAME` | postgres | Database username |
| `DB_PASSWORD` | difypassword | Database password |
| `REDIS_HOST` | redis | Redis hostname |

---

## 5. Architecture

This deployment includes:

| Service | Purpose |
|---------|---------|
| `dify-api` | Backend API server |
| `dify-web` | Frontend web application |
| `db` | PostgreSQL database |
| `redis` | Caching and job queue |

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `postgres_data` | Application data, users, apps |
| `redis_data` | Cache and session data |

---

## 7. Connecting to Local LLMs

In Dify settings, add a custom model provider:

- **Provider Type**: Ollama
- **Base URL**: `http://host.docker.internal:11434`
- **Model**: `llama3.2` (or your preferred model)

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.dify.ai/) | Upstream docs |
| [Dify GitHub](https://github.com/langgenius/dify) | Source code |
| [Ollama](../../ai-ml/llm-inference/ollama/README.md) | LLM backend |
| [Automation & Orchestration](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
