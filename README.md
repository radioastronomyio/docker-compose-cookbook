<!--
---
title: "Docker Compose Cookbook"
description: "Curated Docker Compose configurations for self-hosted services"
author: "VintageDon"
date: "2025-01-04"
version: "3.1"
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
[![Recipes](https://img.shields.io/badge/Recipes-100+-green)]()

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
- Category organization — Services grouped by function for easy discovery

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

| Category | Recipes | Status | Jump |
|----------|---------|--------|------|
| AI & Machine Learning | 21 | Active | [→](#ai--machine-learning) |
| Automation & Orchestration | 8 | Active | [→](#automation--orchestration) |
| Container Management | 3 | Active | [→](#container-management) |
| Databases | 20 | Active | [→](#databases) |
| Development & CI/CD | 9 | Active | [→](#development--cicd) |
| Home Automation | 1 | Active | [→](#home-automation) |
| Media & Entertainment | 8 | Active | [→](#media--entertainment) |
| Messaging & Collaboration | 2 | Active | [→](#messaging--collaboration) |
| Monitoring & Logging | 13 | Active | [→](#monitoring--logging) |
| Networking | 10 | Active | [→](#networking) |
| Personal Utilities | 8 | Active | [→](#personal-utilities) |
| Security | 2 | Active | [→](#security) |
| Storage Solutions | 6 | Active | [→](#storage-solutions) |
| Web Application Servers | 6 | Active | [→](#web-application-servers) |

---

## AI & Machine Learning

Docker Compose recipes for local LLM inference, AI tools, image generation, and machine learning platforms. GPU acceleration supported via NVIDIA Container Toolkit.

| Subcategory | Description | Recipes |
|-------------|-------------|---------|
| [llm-inference](ai-ml/llm-inference/README.md) | LLM inference engines | Ollama, LocalAI, Text-Generation-WebUI, vLLM |
| [chat-interfaces](ai-ml/chat-interfaces/README.md) | Chat UIs and RAG platforms | Open WebUI, LibreChat, AnythingLLM, PrivateGPT |
| [image-generation](ai-ml/image-generation/README.md) | Image synthesis tools | Automatic1111, ComfyUI, Fooocus, InvokeAI, SwarmUI |
| [audio-intelligence](ai-ml/audio-intelligence/README.md) | Speech recognition | Faster Whisper, Wyoming Whisper |
| [document-processing](ai-ml/document-processing/README.md) | Document manipulation with OCR | Stirling-PDF |
| [rag-engines](ai-ml/rag-engines/README.md) | RAG orchestration | RAGFlow |
| [search-engines](ai-ml/search-engines/README.md) | AI-powered search | Perplexica |
| [ai-agents](ai-ml/ai-agents/README.md) | Autonomous AI agents | OpenHands |
| [data-annotation](ai-ml/data-annotation/README.md) | ML data labeling | Label Studio, CVAT |

[→ Full details](ai-ml/README.md)

---

## Automation & Orchestration

Infrastructure automation, workflow engines, and AI agent platforms.

| Recipe | Description |
|--------|-------------|
| [ansibleawx-postgres-redis](automation-orchestration/ansibleawx-postgres-redis/README.md) | Ansible AWX with PostgreSQL and Redis |
| [rundeck](automation-orchestration/rundeck/README.md) | Job scheduler and runbook automation |
| [stackstorm-mongodb-rabbitmq-postgres](automation-orchestration/stackstorm-mongodb-rabbitmq-postgres/README.md) | Event-driven automation platform |
| [n8n](automation-orchestration/n8n/README.md) | Workflow automation with LangChain integration |
| [flowise](automation-orchestration/flowise/README.md) | Low-code LangChain app builder |
| [dify](automation-orchestration/dify/README.md) | GenAI application development platform |
| [changedetection](automation-orchestration/changedetection/README.md) | Website change monitoring |
| [postiz](automation-orchestration/postiz/README.md) | Social media scheduling |

[→ Full details](automation-orchestration/README.md)

---

## Container Management

Container orchestration interfaces and management tools.

| Recipe | Description |
|--------|-------------|
| [portainer](container-management/portainer/README.md) | Container management UI |
| [dockge](container-management/dockge/README.md) | Docker Compose stack manager |
| [watchtower](container-management/watchtower/README.md) | Automated container updates |

[→ Full details](container-management/README.md)

---

## Databases

SQL, NoSQL, time series, vector, and graph databases organized by data model.

| Subcategory | Description | Recipes |
|-------------|-------------|---------|
| [relational](databases/relational/README.md) | SQL databases | MySQL, MariaDB, PostgreSQL, SQLite |
| [document](databases/document/README.md) | Document stores | MongoDB, CouchDB |
| [key-value](databases/key-value/README.md) | In-memory stores | Redis, Dragonfly |
| [graph](databases/graph/README.md) | Graph databases | Neo4j |
| [timeseries](databases/timeseries/README.md) | Time series databases | InfluxDB, QuestDB |
| [vector](databases/vector/README.md) | Vector embeddings for RAG | Qdrant, Milvus, Weaviate, ChromaDB |
| [wide-column](databases/wide-column/README.md) | Wide-column stores | Cassandra |
| [management](databases/management/README.md) | Admin tools | pgAdmin, phpMyAdmin, Mongo Express, Redis Commander |

[→ Full details](databases/README.md)

---

## Development & CI/CD

Git servers, CI/CD pipelines, and development tools.

| Recipe | Description |
|--------|-------------|
| [gitea-mysql](development-ci-cd/gitea-mysql/README.md) | Gitea with MySQL backend |
| [gitea-postgresql](development-ci-cd/gitea-postgresql/README.md) | Gitea with PostgreSQL backend |
| [gitea-sqlite3](development-ci-cd/gitea-sqlite3/README.md) | Gitea with SQLite backend |
| [gitlabce](development-ci-cd/gitlabce/README.md) | GitLab Community Edition |
| [gogs-mysql](development-ci-cd/gogs-mysql/README.md) | Gogs with MySQL backend |
| [gogs-postgres](development-ci-cd/gogs-postgres/README.md) | Gogs with PostgreSQL backend |
| [gogs-sqlite3](development-ci-cd/gogs-sqlite3/README.md) | Gogs with SQLite backend |
| [jenkins-sqlite3](development-ci-cd/jenkins-sqlite3/README.md) | Jenkins CI server |
| [code-server](development-ci-cd/code-server/README.md) | VS Code in the browser |

[→ Full details](development-ci-cd/README.md)

---

## Home Automation

Smart home platforms, IoT, and home infrastructure.

| Recipe | Description |
|--------|-------------|
| [frigate](home-automation/frigate/README.md) | AI-powered NVR with object detection |

Planned: Home Assistant, Node-RED, Mosquitto MQTT.

[→ Full details](home-automation/README.md)

---

## Media & Entertainment

Media servers, photo management, streaming platforms, and the complete *Arr media automation stack.

| Recipe | Description |
|--------|-------------|
| [jellyfin](media-entertainment/jellyfin/README.md) | Open-source media server with GPU transcoding |
| [prowlarr](media-entertainment/prowlarr/README.md) | Indexer manager for *Arr stack |
| [sonarr](media-entertainment/sonarr/README.md) | TV series lifecycle management |
| [radarr](media-entertainment/radarr/README.md) | Movie lifecycle management |
| [jellyseerr](media-entertainment/jellyseerr/README.md) | Media request management |
| [bazarr](media-entertainment/bazarr/README.md) | Subtitle automation |
| [immich](media-entertainment/immich/README.md) | Self-hosted Google Photos alternative |
| [audiobookshelf](media-entertainment/audiobookshelf/README.md) | Audiobook and podcast server |

[→ Full details](media-entertainment/README.md)

---

## Messaging & Collaboration

Push notifications, newsletters, and team communication.

| Recipe | Description |
|--------|-------------|
| [ntfy](messaging-collaboration/ntfy/README.md) | Push notification server |
| [listmonk](messaging-collaboration/listmonk/README.md) | Newsletter and mailing list manager |

[→ Full details](messaging-collaboration/README.md)

---

## Monitoring & Logging

Metrics collection, visualization, log aggregation, and system observability.

| Recipe | Description |
|--------|-------------|
| [Prometheus](monitoring-logging/Prometheus/README.md) | Time series metrics database |
| [grafana](monitoring-logging/grafana/README.md) | Metrics visualization |
| [graylog-elasticsearch-mongodb](monitoring-logging/graylog-elasticsearch-mongodb/README.md) | Centralized log management |
| [fluentd](monitoring-logging/fluentd/README.md) | Unified logging layer |
| [cacti-mysql](monitoring-logging/cacti-mysql/README.md) | Network graphing with RRDtool |
| [uptime-kuma](monitoring-logging/uptime-kuma/README.md) | Status monitoring |
| [beszel](monitoring-logging/beszel/README.md) | Lightweight server monitoring |
| [glitchtip](monitoring-logging/glitchtip/README.md) | Error tracking (Sentry alternative) |
| [homarr](monitoring-logging/homarr/README.md) | Dashboard for self-hosted services |
| [scrutiny](monitoring-logging/scrutiny/README.md) | Hard drive S.M.A.R.T. monitoring |
| [netdata](monitoring-logging/netdata/README.md) | Real-time performance monitoring |
| [dozzle](monitoring-logging/dozzle/README.md) | Real-time container log viewer |
| [matomo](monitoring-logging/matomo/README.md) | Web analytics (Google Analytics alternative) |

[→ Full details](monitoring-logging/README.md)

---

## Networking

VPNs, DNS servers, reverse proxies, ad blocking, and network tools.

| Recipe | Description |
|--------|-------------|
| [adguard-home](networking/adguard-home/README.md) | Network-wide ad blocking |
| [pihole](networking/pihole/README.md) | DNS-based ad blocking |
| [wireguard](networking/wireguard/README.md) | Modern VPN tunnel |
| [openvpn](networking/openvpn/README.md) | OpenVPN server |
| [softethervpn](networking/softethervpn/README.md) | Multi-protocol VPN server |
| [searxng](networking/searxng/README.md) | Privacy-respecting metasearch engine |
| [nginx-proxy-manager](networking/nginx-proxy-manager/README.md) | Reverse proxy with GUI |
| [traefik](networking/traefik/README.md) | Cloud-native edge router |
| [headscale](networking/headscale/README.md) | Self-hosted Tailscale control server |
| [guacamole](networking/guacamole/README.md) | Clientless remote desktop gateway |

[→ Full details](networking/README.md)

---

## Personal Utilities

Knowledge management, productivity tools, and personal finance.

| Recipe | Description |
|--------|-------------|
| [bookstack](personal-utilities/bookstack/README.md) | Wiki and documentation platform |
| [linkwarden](personal-utilities/linkwarden/README.md) | Bookmark manager with archival |
| [excalidraw](personal-utilities/excalidraw/README.md) | Virtual whiteboard |
| [firefly-iii](personal-utilities/firefly-iii/README.md) | Personal finance manager |
| [it-tools](personal-utilities/it-tools/README.md) | Developer utilities collection |
| [hoarder](personal-utilities/hoarder/README.md) | Bookmark and read-later app |
| [mealie](personal-utilities/mealie/README.md) | Recipe manager |
| [actual-budget](personal-utilities/actual-budget/README.md) | Budget tracking |

[→ Full details](personal-utilities/README.md)

---

## Security

Authentication, secrets management, and password vaults.

| Recipe | Description |
|--------|-------------|
| [authentik](security/authentik/README.md) | Identity provider and SSO |
| [vaultwarden](security/vaultwarden/README.md) | Bitwarden-compatible password manager |

[→ Full details](security/README.md)

---

## Storage Solutions

File synchronization, backup tools, and document management.

| Recipe | Description |
|--------|-------------|
| [nextcloud-aio](storage-solutions/nextcloud-aio/README.md) | Self-hosted cloud storage |
| [paperless-ngx](storage-solutions/paperless-ngx/README.md) | Document management system |
| [filebrowser](storage-solutions/filebrowser/README.md) | Web file manager |
| [pingvin-share](storage-solutions/pingvin-share/README.md) | File sharing (WeTransfer alternative) |
| [syncthing](storage-solutions/syncthing/README.md) | Decentralized file sync |
| [duplicati](storage-solutions/duplicati/README.md) | Encrypted backup solution |

[→ Full details](storage-solutions/README.md)

---

## Web Application Servers

CMS platforms, no-code databases, and business applications.

| Recipe | Description |
|--------|-------------|
| [ghost](web-application-servers/ghost/README.md) | Professional publishing platform |
| [baserow](web-application-servers/baserow/README.md) | No-code database (Airtable alternative) |
| [invoice-ninja](web-application-servers/invoice-ninja/README.md) | Invoicing and billing |
| [docmost](web-application-servers/docmost/README.md) | Documentation platform |
| [penpot](web-application-servers/penpot/README.md) | Design platform (Figma alternative) |
| [twenty](web-application-servers/twenty/README.md) | CRM platform |

[→ Full details](web-application-servers/README.md)

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/radioastronomyio/docker-compose-cookbook.git
cd docker-compose-cookbook

# Navigate to desired recipe
cd media-entertainment/jellyfin

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
├── README.md             # Quick start and overview
├── docs/                 # Extended documentation (optional)
│   ├── CONFIGURATION.md
│   ├── SECURITY.md
│   └── TROUBLESHOOTING.md
└── scripts/              # Helper scripts (optional)
```

---

## 🔧 Requirements

| Requirement | Version | Notes |
|-------------|---------|-------|
| Docker Engine | 20.10+ | [Install guide](https://docs.docker.com/engine/install/) |
| Docker Compose | v2+ | Included with Docker Desktop; [standalone install](https://docs.docker.com/compose/install/) |
| Git | Any | For cloning the repository |
| NVIDIA Container Toolkit | Latest | Required for GPU-accelerated recipes |

---

## 🤝 OSS Program Support

This repository benefits from open source programs that provide tooling to qualifying public repositories.

| Program | Provides | Use Case |
|---------|----------|----------|
| [Greptile](https://greptile.com) | AI code review | PR review, codebase Q&A |
| [Atlassian](https://www.atlassian.com/software/views/open-source-license-request) | Jira, Confluence | Project tracking, documentation |

---

## 🌟 Open Science Philosophy

We practice open science and open methodology — our version of "showing your work":

- Research methodologies are fully documented and repeatable
- Infrastructure configurations are version-controlled and automated
- Scripts and pipelines are published so others can learn, adapt, or improve them
- Learning processes are captured and shared for community benefit

All projects operate under open source licenses (primarily MIT) to ensure maximum reproducibility.

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

Last Updated: January 4, 2025 | 100+ Active Recipes | 14 Categories
