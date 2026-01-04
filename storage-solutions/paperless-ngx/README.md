<!--
---
title: "Paperless-ngx Docker Setup"
description: "Docker Compose deployment for Paperless-ngx document management"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: paperless-ngx
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://docs.paperless-ngx.com/)"
---
-->

# Paperless-ngx Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Paperless-ngx transforms physical paper into searchable digital archives via OCR. It automatically processes, categorizes, and indexes documents, making your paperless office a reality.

---

## 1. Contents

```
paperless-ngx/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- ~2GB RAM for OCR processing

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Generate secret: `openssl rand -base64 32`
3. Set `PAPERLESS_SECRET` and `ADMIN_PASSWORD`
4. Run `docker compose up -d`
5. Access UI at `http://localhost:8000`

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `PAPERLESS_PORT` | 8000 | Web UI port |
| `PAPERLESS_SECRET` | - | Django secret key (required) |
| `ADMIN_USER` | admin | Initial admin username |
| `ADMIN_PASSWORD` | - | Initial admin password |
| `OCR_LANGUAGE` | eng | OCR language(s) |
| `TZ` | America/New_York | Timezone |

---

## 5. Architecture

| Service | Purpose |
|---------|---------|
| `webserver` | Django application, OCR processing |
| `broker` | Redis task queue |
| `gotenberg` | Office document → PDF conversion |
| `tika` | Text extraction from complex formats |

---

## 6. Document Workflow

1. **Consume**: Drop files into `./consume/` directory
2. **Process**: Paperless OCRs images and PDFs
3. **Extract**: Tika handles Word, Excel, PowerPoint
4. **Convert**: Gotenberg creates PDF/A for archival
5. **Index**: Full-text search via Whoosh or Elasticsearch
6. **Classify**: Auto-tagging via ML (optional)

---

## 7. Directory Structure

| Path | Purpose |
|------|---------|
| `./consume/` | Inbox for automatic import |
| `./media/` | Processed document storage |
| `./data/` | Database and search index |
| `./export/` | Manual export destination |

---

## 8. Supported Formats

| Format | Handler |
|--------|---------|
| PDF | Native OCR |
| Images (JPG, PNG, TIFF) | Native OCR |
| Word (.docx) | Tika |
| Excel (.xlsx) | Tika |
| PowerPoint (.pptx) | Tika |
| Email (.eml) | Tika |
| Plain text | Native |

---

## 9. OCR Languages

Install additional languages with `OCR_LANGUAGE`:

```bash
# Single language
OCR_LANGUAGE=deu

# Multiple languages
OCR_LANGUAGE=eng+deu+fra
```

---

## 10. Scanner Integration

Paperless-ngx works with any scanner that can output to a folder:

- Network scanners → SMB share → consume folder
- Phone apps (Genius Scan, Adobe Scan) → sync to consume
- Email → IMAP consumption (configure in settings)

---

## 11. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://docs.paperless-ngx.com/) | Upstream docs |
| [Storage Solutions](../README.md) | Parent category |
| [Nextcloud AIO](../nextcloud-aio/README.md) | File sync integration |

---

## 12. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
