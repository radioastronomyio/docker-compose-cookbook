<!--
---
title: "Invoice Ninja Docker Setup"
description: "Docker Compose deployment for Invoice Ninja enterprise invoicing platform"
author: "VintageDon"
date: "2025-01-04"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: web-application-servers
  - tech: invoice-ninja
related_documents:
  - "[Web Application Servers README](../README.md)"
  - "[Official Docs](https://invoiceninja.github.io/)"
---
-->

# Invoice Ninja Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Invoice Ninja is a comprehensive suite for invoicing, quoting, and payment collection. It targets freelancers and small businesses, providing professional-grade financial document generation with self-hosted data sovereignty.

---

## 1. Contents

```
invoice-ninja/
├── docker-compose.yml  # Main compose file
├── nginx.conf          # Web server configuration
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Generated APP_KEY

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate APP_KEY: `docker run --rm -it invoiceninja/invoiceninja php artisan key:generate --show`
3. Create nginx.conf (see below)
4. Run `docker compose up -d`
5. Access web UI at `http://localhost:8091`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `APP_URL` | `http://localhost:8091` | Public application URL |
| `APP_KEY` | - | Encryption key (generate before first run) |
| `DB_PASS` | - | MySQL database password |
| `DB_ROOT_PASS` | - | MySQL root password |

### Critical: APP_KEY Generation

The APP_KEY must be generated prior to deployment. It encrypts sensitive data in the database. Losing this key means losing access to encrypted data.

```bash
docker run --rm -it invoiceninja/invoiceninja php artisan key:generate --show
```

### Architecture

Invoice Ninja is a 3-tier "Micro-SaaS" stack:
- **invoiceninja**: PHP application logic
- **in_web**: Nginx serving static assets
- **in_db**: MySQL 8 database

Shared volumes enable Nginx to serve images/CSS while PHP handles logic.

---

## 5. Nginx Configuration

Create `nginx.conf` in the recipe directory:

```nginx
events {
    worker_connections 1024;
}

http {
    include /etc/nginx/mime.types;
    
    server {
        listen 80;
        root /var/www/app/public;
        index index.php;

        location / {
            try_files $uri $uri/ /index.php?$query_string;
        }

        location ~ \.php$ {
            fastcgi_pass invoiceninja:9000;
            fastcgi_index index.php;
            include fastcgi_params;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        }
    }
}
```

---

## 6. Data Persistence

| Volume | Purpose |
|--------|---------|
| `./in_public` | Public assets (shared with Nginx) |
| `./in_storage` | Uploads and generated files |
| `in_db_data` | MySQL database |

---

## 7. Port Reference

| Port | Protocol | Purpose |
|------|----------|---------|
| 8091 | TCP | Web UI |

---

## 8. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://invoiceninja.github.io/) | Upstream docs |
| [Firefly III](../../personal-utilities/firefly-iii/README.md) | Personal finance |
| [Web Application Servers](../README.md) | Parent category |

---

## 9. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
