<!--
---
title: "Actual Budget Docker Setup"
description: "Docker Compose deployment for Actual Budget personal finance"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: actual-budget
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://actualbudget.org/docs/)"
---
-->

# Actual Budget Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Actual Budget is a local-first personal finance application. The server acts as a sync relay while your budget data lives on your devices, ensuring fast performance and privacy.

---

## 1. Contents

```
actual-budget/
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

1. Copy `.env.example` to `.env`
2. Run `docker compose up -d`
3. Access UI at `http://localhost:5006`
4. Create a new budget or import from YNAB
5. Set up accounts and categories

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `ACTUAL_PORT` | 5006 | Web UI port |

Actual Budget requires minimal configuration due to its local-first design.

---

## 5. Local-First Architecture

Unlike cloud-based budgeting apps:

| Aspect | Traditional | Actual Budget |
|--------|-------------|---------------|
| Data location | Server | Your devices |
| Server role | Database | Sync relay |
| Offline support | Limited | Full functionality |
| Performance | Network dependent | Instant |
| Privacy | Server has data | Data on your devices |

The server synchronizes changes between devices but is not the source of truth.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| Envelope Budgeting | YNAB-style budget categories |
| Bank Sync | Import transactions (manual or automated) |
| Reports | Spending analysis and trends |
| Goals | Savings targets and tracking |
| Scheduling | Recurring transactions |
| Multi-device | Sync across devices |
| YNAB Import | Migrate from YNAB4/nYNAB |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `actual-data` | Sync database and server config |

Your actual budget data is stored on each client device, not primarily on the server.

---

## 8. Bank Sync Options

| Method | Description |
|--------|-------------|
| Manual Import | Download QFX/OFX from bank, import |
| GoCardless | European bank integration (free) |
| SimpleFIN | US bank integration (paid service) |

Bank sync is optional; manual entry works perfectly.

---

## 9. YNAB Comparison

| Aspect | Actual | YNAB |
|--------|--------|------|
| Cost | Free (self-hosted) | $99/year |
| Data ownership | Full | YNAB servers |
| Offline | Full support | Limited |
| Bank sync | Optional add-ons | Built-in (US) |
| Mobile | PWA | Native apps |

Actual originated as a YNAB alternative with local-first philosophy.

---

## 10. Mobile Access

Actual is a Progressive Web App:

1. Open in mobile browser
2. Add to Home Screen
3. Works offline with synced data

No native app required.

---

## 11. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://actualbudget.org/docs/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 12. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
