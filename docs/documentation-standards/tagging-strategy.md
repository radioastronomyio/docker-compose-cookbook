<!--
---
title: "Tagging Strategy"
description: "Controlled vocabulary for document classification and RAG retrieval in docker-compose-cookbook"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
tags:
  - domain: documentation
  - type: specification
related_documents:
  - "[Interior README Template](interior-readme-template.md)"
  - "[General KB Template](general-kb-template.md)"
  - "[Recipe README Template](recipe-readme-template.md)"
---
-->

# Tagging Strategy

## 1. Purpose

This document defines the controlled tag vocabulary for all documentation in docker-compose-cookbook, enabling consistent classification for human navigation and RAG system retrieval.

---

## 2. Scope

Covers all tag categories, valid values, and usage guidance. Does not cover front-matter field structure—see individual templates for field requirements.

---

## 3. Tag Categories

### Category Tags

Primary organizational category. Usually one per document.

| Tag | Description |
|-----|-------------|
| `databases` | Database deployments and management tools |
| `networking` | VPNs, DNS, proxies, network infrastructure |
| `monitoring-logging` | Observability, metrics, log aggregation |
| `automation-orchestration` | Ansible, runbooks, workflow automation |
| `development-ci-cd` | Git servers, CI/CD pipelines, dev tools |
| `storage-solutions` | Object storage, file sync, backup |
| `security` | Auth, secrets management, vulnerability scanning |
| `container-management` | Container orchestration and management UIs |
| `web-application-servers` | Reverse proxies, web servers, load balancers |
| `messaging-collaboration` | Chat, email, team communication |
| `home-automation` | Smart home, IoT platforms |
| `media-entertainment` | Media servers, streaming, *arr stack |
| `ai-ml` | LLM inference, ML tools, AI platforms |
| `data-pipelines` | Workflow orchestration, ETL, data processing |

**Usage**: Choose the primary category. A recipe for Grafana is `monitoring-logging`, not `databases` even if it uses a database.

---

### Subcategory Tags (Databases)

Specific to the `databases` category.

| Tag | Description |
|-----|-------------|
| `relational` | SQL databases (MySQL, PostgreSQL, MariaDB, SQLite) |
| `document` | Document stores (MongoDB, CouchDB) |
| `key-value` | Key-value stores (Redis, DragonFly, Memcached) |
| `graph` | Graph databases (Neo4j) |
| `timeseries` | Time series databases (InfluxDB, QuestDB) |
| `vector` | Vector databases (Qdrant, Milvus, Weaviate, Chroma) |
| `wide-column` | Wide-column stores (Cassandra) |
| `management` | Database admin tools (phpMyAdmin, pgAdmin) |

**Usage**: Tag database recipes with the appropriate subcategory.

---

### Type Tags

Document purpose and structure.

| Tag | Description |
|-----|-------------|
| `directory-readme` | README for a directory (interior READMEs) |
| `recipe` | Individual docker-compose recipe |
| `guide` | Step-by-step procedures |
| `reference` | Lookup information (data dictionary, schema) |
| `specification` | Formal requirements or standards |
| `worklog` | Work log milestone documentation |

**Usage**: One type per document. Recipe READMEs get `recipe`, category READMEs get `directory-readme`.

---

### Tech Tags

Technologies and services. Tag with specific services involved.

| Tag | Description |
|-----|-------------|
| `docker` | Docker-related |
| `compose` | Docker Compose specific |
| `traefik` | Traefik reverse proxy |
| `nginx` | Nginx web server |
| `postgres` | PostgreSQL database |
| `mysql` | MySQL database |
| `redis` | Redis cache/store |
| `prometheus` | Prometheus metrics |
| `grafana` | Grafana dashboards |
| `ollama` | Ollama LLM inference |

**Usage**: Tag when the document is specific to that technology. Add tech tags as needed—this list is not exhaustive.

---

### Status Tags

Document lifecycle status.

| Tag | Description |
|-----|-------------|
| `active` | Current, maintained |
| `wip` | Work in progress |
| `planned` | Placeholder, not yet implemented |
| `deprecated` | No longer maintained |
| `archived` | Historical reference only |

**Usage**: One status per document.

---

### Audience Tags

Target reader expertise level.

| Tag | Description |
|-----|-------------|
| `beginners` | New to Docker/self-hosting |
| `intermediate` | Comfortable with Docker, some ops experience |
| `advanced` | Production experience, complex deployments |
| `all` | Applicable to all skill levels |

**Usage**: Tag when audience-specific content exists.

---

## 4. Examples

### Recipe README

```yaml
tags:
  - type: recipe
  - category: databases
  - subcategory: relational
  - tech: [postgres, docker, compose]
  - status: active
```

### Category README

```yaml
tags:
  - type: directory-readme
  - category: monitoring-logging
  - status: active
```

### Guide Document

```yaml
tags:
  - type: guide
  - category: networking
  - tech: [traefik, docker]
  - audience: intermediate
  - status: active
```

---

## 5. References

| Reference | Link |
|-----------|------|
| Interior README Template | [interior-readme-template.md](interior-readme-template.md) |
| Recipe README Template | [recipe-readme-template.md](recipe-readme-template.md) |
| General KB Template | [general-kb-template.md](general-kb-template.md) |

---
