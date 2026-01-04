<!--
---
title: "Mealie Docker Setup"
description: "Docker Compose deployment for Mealie recipe manager"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: personal-utilities
  - tech: mealie
related_documents:
  - "[Personal Utilities README](../README.md)"
  - "[Official Docs](https://docs.mealie.io/)"
---
-->

# Mealie Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Mealie is a self-hosted recipe manager that imports recipes from URLs, stripping ads and standardizing metadata. It provides meal planning, shopping lists, and a clean interface for your personal cookbook.

---

## 1. Contents

```
mealie/
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
3. Access UI at `http://localhost:9925`
4. Create admin account
5. Start importing recipes

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `MEALIE_PORT` | 9925 | Web UI port |
| `ALLOW_SIGNUP` | true | Allow new registrations |
| `PUID` | 1000 | User ID |
| `PGID` | 1000 | Group ID |
| `TZ` | America/New_York | Timezone |

---

## 5. Recipe Import

Mealie extracts structured recipe data (Schema.org/Recipe) from URLs:

1. Click "Create" → "Import"
2. Paste recipe URL
3. Mealie extracts ingredients, instructions, images
4. Edit and save

Supported sites include AllRecipes, Food Network, Serious Eats, and most sites with proper recipe markup.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| URL Import | Extract recipes from websites |
| Meal Planning | Weekly/monthly meal calendars |
| Shopping Lists | Auto-generate from meal plans |
| Scaling | Adjust serving sizes |
| Categories & Tags | Organize your cookbook |
| Nutritional Info | Auto-calculated when available |
| Print View | Clean printing format |
| API | REST API for integrations |

---

## 7. Data Persistence

| Volume | Purpose |
|--------|---------|
| `mealie-data` | SQLite database, images, backups |

---

## 8. Database Options

Default SQLite works well for personal use. For families or heavy use, PostgreSQL is recommended:

```yaml
environment:
  - DB_ENGINE=postgres
  - POSTGRES_USER=mealie
  - POSTGRES_PASSWORD=secure_password
  - POSTGRES_SERVER=db
  - POSTGRES_DB=mealie
```

Add a PostgreSQL service to the compose file.

---

## 9. Backup & Restore

Mealie includes built-in backup:

1. Go to Settings → Backups
2. Create backup (exports JSON + images)
3. Download backup file
4. Restore via Settings → Backups → Import

---

## 10. Mobile Access

Mealie is a Progressive Web App (PWA):

1. Open Mealie in mobile browser
2. Add to Home Screen
3. Use like a native app

Works offline with cached recipes.

---

## 11. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.mealie.io/) | Upstream docs |
| [Personal Utilities](../README.md) | Parent category |

---

## 12. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
