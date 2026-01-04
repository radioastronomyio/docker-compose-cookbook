<!--
---
title: "OpenHands Docker Setup"
description: "Docker Compose deployment for OpenHands autonomous coding agent"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: ai-ml
  - subcategory: ai-agents
  - tech: openhands
related_documents:
  - "[AI Agents README](../README.md)"
  - "[Official Docs](https://docs.openhands.dev/)"
---
-->

# OpenHands Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

OpenHands (formerly OpenDevin) is an autonomous software engineering agent capable of executing shell commands, browsing the web, and editing files to solve complex engineering tasks. Unlike copilots that autocomplete text, OpenHands performs real work in sandboxed containers.

---

## 1. Contents

```
openhands/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Ollama running on host (or OpenAI API key)
- Sufficient disk space for sandbox images (~5GB)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Set `WORKSPACE_BASE` to an absolute path on your host
3. Set `SANDBOX_USER_ID` to your user ID (`id -u`)
4. Run `docker compose up -d`
5. Access UI at `http://localhost:3000`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `OPENHANDS_PORT` | 3000 | Web UI port |
| `WORKSPACE_BASE` | ./workspace | Host directory for generated code |
| `SANDBOX_USER_ID` | 1000 | Host user ID for file permissions |
| `OLLAMA_PORT` | 11434 | Ollama API port |
| `LOG_ALL_EVENTS` | true | Verbose agent logging |

---

## 5. Security Considerations

⚠️ **Critical Security Warning**

OpenHands requires Docker socket access to spawn sandbox containers. This grants the container root-equivalent privileges on the host Docker daemon.

**Mandatory precautions:**

- Never expose port 3000 to the public internet
- Run behind VPN, SSH tunnel, or strict firewall
- Consider using Docker socket proxy for additional isolation
- Review agent actions in the workspace directory

---

## 6. Sandboxing Architecture

OpenHands uses the "sidecar sandbox" pattern:

1. Agent container receives task
2. Agent spawns isolated runtime container via Docker socket
3. Code execution occurs in runtime container
4. Results written to mounted workspace
5. Runtime container destroyed after task

This isolates potentially unsafe code from the main application.

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `openhands_state` | Agent state, conversation history |
| `${WORKSPACE_BASE}` | Host-mounted directory for generated code |

The workspace persists on the host filesystem, surviving container recreation.

---

## 8. LLM Configuration

OpenHands supports multiple LLM backends. Configure via UI after first launch:

| Backend | Configuration |
|---------|--------------|
| Ollama | `http://host.docker.internal:11434` (default) |
| OpenAI | Set API key in UI settings |
| Anthropic | Set API key in UI settings |

For best results with coding tasks, use capable models like `deepseek-coder`, `codellama`, or `gpt-4`.

---

## 9. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.openhands.dev/) | Upstream docs |
| [GitHub Repository](https://github.com/OpenHands/OpenHands) | Source code |
| [AI Agents](../README.md) | Parent category |
| [Ollama](../../llm-inference/ollama/README.md) | Recommended LLM backend |

---

## 10. License

This project is licensed under the MIT License - see the [LICENSE](../../../LICENSE) file for details.
