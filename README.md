<!--
---
title: "Docker Compose Cookbook"
description: "Curated Docker Compose configurations for self-hosted services"
author: "VintageDon"
date: "2025-01-02"
version: "2.0"
status: "Active"
tags:
  - type: project-root
  - domain: [docker, self-hosting, homelab]
  - tech: [docker, compose, yaml]
related_documents:
  - "[Docker Compose Docs](https://docs.docker.com/compose/)"
  - "[RadioAstronomy.io](https://github.com/radioastronomyio)"
---
-->

# 🐳 Docker Compose Cookbook

![Repository Banner](assets/repo-banner.jpg)

[![Docker](https://img.shields.io/badge/Docker-20.10+-2496ED?logo=docker)](https://www.docker.com/)
[![Compose](https://img.shields.io/badge/Compose-v2-2496ED?logo=docker)](https://docs.docker.com/compose/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Recipes](https://img.shields.io/badge/Recipes-30+-green)]()

> Curated Docker Compose configurations for self-hosted services, organized by category with comprehensive documentation.

This cookbook provides copy-and-deploy Docker Compose configurations for common infrastructure services. Each recipe includes sensible defaults, environment templates, and documentation covering configuration, security, performance tuning, and troubleshooting. Clone a recipe, customize the `.env` file, and deploy in minutes.

---

## 🔭 Background

![alt text](assets/docker-compose-cookbook-primary-infographic.jpg)

Self-hosting services requires researching Docker configurations, understanding environment variables, and troubleshooting deployment issues. This friction slows adoption and leads to inconsistent setups across environments.

The Docker Compose Cookbook addresses this by providing:

- Standardized recipes — Every recipe follows the same structure, so once you've used one, you understand them all
- Comprehensive documentation — Each recipe includes configuration guides, security considerations, and troubleshooting help
- Sensible defaults — Configurations work out of the box while remaining customizable
- Category organization — Services grouped by function (databases, networking, monitoring, etc.) for easy discovery

The cookbook covers 14 categories spanning databases, networking, CI/CD, monitoring, AI/ML tools, and more — reflecting the needs of modern home labs and small-team infrastructure.

---

## 🎯 Target Audience

| Audience | Use Case |
|----------|----------|
| Home Lab Enthusiasts | Deploy self-hosted alternatives to cloud services |
| DevOps Learners | Learn Docker Compose patterns through working examples |
| Small Teams | Quick infrastructure setup without enterprise complexity |
| Developers | Local development environments mirroring production |

---

## 📦 Categories

### Active Categories (with recipes)

| Category | Description | Recipes |
|----------|-------------|---------|
| [databases/](databases/README.md) | SQL, NoSQL, time series, vector, and graph databases | 9 |
| [networking/](networking/README.md) | VPNs, DNS, ad blocking | 5 |
| [monitoring-logging/](monitoring-logging/README.md) | Metrics, visualization, log aggregation | 5 |
| [automation-orchestration/](automation-orchestration/README.md) | Ansible, Rundeck, StackStorm | 3 |
| [development-ci-cd/](development-ci-cd/README.md) | Git servers, CI/CD pipelines | 8 |

### Planned Categories

| Category | Description | Planned Recipes |
|----------|-------------|-----------------|
| [storage-solutions/](storage-solutions/README.md) | Object storage, file sync, backup | MinIO, Nextcloud, Syncthing |
| [security/](security/README.md) | Auth, secrets, vulnerability scanning | Keycloak, Authelia, Vaultwarden |
| [container-management/](container-management/README.md) | Container orchestration UIs | Portainer, Dockge, Watchtower |
| [web-application-servers/](web-application-servers/README.md) | Reverse proxies, load balancers | Traefik, Caddy, Nginx Proxy Manager |
| [messaging-collaboration/](messaging-collaboration/README.md) | Chat, email platforms | Matrix, Mattermost, Mailcow |
| [home-automation/](home-automation/README.md) | Smart home, IoT | Home Assistant, Node-RED, Mosquitto |
| [media-entertainment/](media-entertainment/README.md) | Media servers, streaming | Jellyfin, Plex, *arr stack |
| [ai-ml/](ai-ml/README.md) | LLM inference, ML tools | Ollama, Open-WebUI, ComfyUI |
| [data-pipelines/](data-pipelines/README.md) | Workflow orchestration, ETL | Airflow, n8n, Dagster |

---

## 🗄️ Database Subcategories

The `databases/` category uses subcategories organized by data model:

| Subcategory | Description | Recipes |
|-------------|-------------|---------|
| [relational/](databases/relational/README.md) | SQL databases (MySQL, MariaDB, PostgreSQL, SQLite) | 3 active, 1 planned |
| [document/](databases/document/README.md) | Document stores (MongoDB, CouchDB) | 2 |
| [key-value/](databases/key-value/README.md) | In-memory stores (Redis, DragonFly) | 1 active, 1 planned |
| [graph/](databases/graph/README.md) | Graph databases (Neo4j) | 1 |
| [timeseries/](databases/timeseries/README.md) | Time series (InfluxDB, QuestDB) | 1 active, 1 planned |
| [vector/](databases/vector/README.md) | Vector databases (Qdrant, Milvus, Weaviate, Chroma) | 4 planned |
| [wide-column/](databases/wide-column/README.md) | Wide-column stores (Cassandra) | 1 |
| [management/](databases/management/README.md) | Admin tools (phpMyAdmin, pgAdmin) | 4 planned |

---

## 📁 Repository Structure

```
docker-compose-cookbook/
├── databases/                    # Database recipes (8 subcategories)
├── networking/                   # VPN, DNS, ad blocking
├── monitoring-logging/           # Observability stack
├── automation-orchestration/     # Infrastructure automation
├── development-ci-cd/            # Git servers, CI/CD
├── storage-solutions/            # Object storage, sync (planned)
├── security/                     # Auth, secrets (planned)
├── container-management/         # Container UIs (planned)
├── web-application-servers/      # Reverse proxies (planned)
├── messaging-collaboration/      # Chat, email (planned)
├── home-automation/              # Smart home (planned)
├── media-entertainment/          # Media servers (planned)
├── ai-ml/                        # LLM, ML tools (planned)
├── data-pipelines/               # Workflow orchestration (planned)
├── docs/
│   └── documentation-standards/  # Templates and guidelines
├── skeleton/                     # Template for new recipes
├── work-logs/                    # Development phases
├── LICENSE
└── README.md                     # This file
```

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/radioastronomyio/docker-compose-cookbook.git
cd docker-compose-cookbook

# Navigate to desired recipe
cd databases/relational/mysql

# Copy and customize environment
cp .env.example .env
nano .env  # or your preferred editor

# Deploy
docker compose up -d

# Verify
docker compose ps
docker compose logs
```

---

## 📋 Recipe Structure

Every recipe follows a standardized structure:

```
recipe-name/
├── docker-compose.yml    # Main compose configuration
├── .env.example          # Environment template (copy to .env)
├── .gitignore            # Excludes .env and local files
├── README.md             # Quick start and overview
├── docs/
│   ├── CONFIGURATION.md  # Detailed configuration options
│   ├── SECURITY.md       # Security hardening guidance
│   ├── PERFORMANCE_TUNING.md
│   ├── TROUBLESHOOTING.md
│   └── UPGRADING.md
├── scripts/              # Helper scripts (optional)
└── LICENSE
```

---

## 🔧 Requirements

| Requirement | Version | Notes |
|-------------|---------|-------|
| Docker Engine | 20.10+ | [Install guide](https://docs.docker.com/engine/install/) |
| Docker Compose | v2+ | Included with Docker Desktop; [standalone install](https://docs.docker.com/compose/install/) |
| Git | Any | For cloning the repository |

---

## 🤝 OSS Program Support

This repository benefits from open source programs that provide tooling to qualifying public repositories.

### Active Programs

| Program | Provides | Use Case |
|---------|----------|----------|
| [Greptile](https://greptile.com) | AI code review | PR review, codebase Q&A |
| [Atlassian](https://www.atlassian.com/software/views/open-source-license-request) | Jira, Confluence (Standard) | Project tracking, documentation |

### Available for Future Use

| Program | Provides | Planned Use |
|---------|----------|-------------|
| [Snyk](https://snyk.io/plans/) | Security scanning | Dependency vulnerability detection |
| [SonarCloud](https://www.sonarsource.com/open-source-editions/) | Code quality | Static analysis |
| [Sentry](https://sentry.io/for/open-source/) | Error tracking | Runtime monitoring |
| [Datadog](https://www.datadoghq.com/partner/open-source/) | Observability | Metrics, logs, APM |

---

## 🌟 Open Science Philosophy

We practice open science and open methodology — our version of "showing your work":

- Research methodologies are fully documented and repeatable
- Infrastructure configurations are version-controlled and automated
- Scripts and pipelines are published so others can learn, adapt, or improve them
- Learning processes are captured and shared for community benefit

Our hope is that these materials help someone facing similar challenges, or inspire collaboration that helps us. All projects operate under open source licenses (primarily MIT) to ensure maximum reproducibility.

---

## 🤝 Contributing

Contributions are welcome! To add a new recipe:

1. Copy the `skeleton/` template to the appropriate category
2. Customize the compose file and documentation
3. Test the deployment locally
4. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

[MIT](LICENSE) © 2025 VintageDon

---

## 🙏 Acknowledgments

- [Docker](https://www.docker.com/) — Container platform
- [LinuxServer.io](https://www.linuxserver.io/) — Well-maintained Docker images
- [Awesome-Selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) — Self-hosting inspiration
- [RadioAstronomy.io](https://github.com/radioastronomyio) — Research organization

---

Last Updated: January 2, 2025 | 30 Active Recipes | 14 Categories
