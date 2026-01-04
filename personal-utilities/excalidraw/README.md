<!--
---
title: "Excalidraw Docker Setup"
description: "Docker Compose deployment for Excalidraw virtual whiteboard"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: excalidraw
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://docs.excalidraw.com/)"
---
-->

# Excalidraw Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Excalidraw is a virtual whiteboard tool that allows for sketching diagrams with a hand-drawn feel. It is widely used in software architecture planning, brainstorming sessions, and technical documentation.

---

## 1. Contents

```
excalidraw/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+

---

## 3. Quick Start

1. Copy `.env.example` to `.env` (no required variables)
2. Run `docker compose up -d`
3. Access web UI at `http://localhost:3003`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `NODE_ENV` | production | Node environment |

### Stateless Architecture

The Excalidraw container is largely stateless for client-side drawing features. The "state" of a drawing is maintained in the user's browser local storage or exported as a `.excalidraw` JSON file. This makes the container incredibly lightweight and resilient.

For real-time multi-user collaboration, a separate WebSocket signaling server is required, but this standalone image provides full "Pro" features for individual use and screen sharing.

---

## 5. Data Persistence

No server-side persistence required. Drawings are stored client-side or exported as files.

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 3003 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.excalidraw.com/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
