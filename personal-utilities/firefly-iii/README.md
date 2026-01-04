<!--
---
title: "Firefly III Docker Setup"
description: "Docker Compose deployment for Firefly III personal finance manager"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: firefly-iii
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://docs.firefly-iii.org/)"
---
-->

# Firefly III Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Firefly III is a strict double-entry bookkeeping system for personal finance. It allows users to track expenses, budgets, and liabilities with granular precision. Self-hosting ensures your financial data remains private and never leaves your infrastructure.

---

## 1. Contents

```
firefly-iii/
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

1. Copy `.env.example` to `.env` and adjust variables
2. Generate APP_KEY: exactly 32 random characters
3. Run `docker compose up -d`
4. Access web UI at `http://localhost:8092`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `APP_KEY` | - | Encryption key (must be exactly 32 characters) |
| `DB_PASS` | - | MariaDB database password |

### Critical: APP_KEY Requirement

The `APP_KEY` must be exactly 32 characters. Generate with: `head /dev/urandom | tr -dc A-Za-z0-9 | head -c 32`

This key encrypts sensitive data in the database. Losing it means losing access to encrypted data.

---

## 5. Data Persistence

| Volume | Purpose |
|--------|---------|
| `firefly_upload` | Uploaded attachments and documents |
| `firefly_db_data` | MariaDB database |

---

## 6. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8092 | TCP | Web UI |

---

## 7. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.firefly-iii.org/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 8. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
