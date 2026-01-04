<!--
---
title: "FileBrowser Docker Setup"
description: "Docker Compose deployment for FileBrowser web file manager"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: storage-solutions
  - tech: filebrowser
related_documents:
  - "[Storage Solutions README](../README.md)"
  - "[Official Docs](https://filebrowser.org/)"
---
-->

# FileBrowser Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

FileBrowser is a lightweight web-based file manager. When you just need to browse, upload, and download files without Nextcloud's complexity, FileBrowser provides a clean interface with minimal overhead.

---

## 1. Contents

```
filebrowser/
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
2. Set `FILE_ROOT` to your files directory
3. Run `docker compose up -d`
4. Access UI at `http://localhost:8080`
5. Login with `admin` / `admin`
6. **Change password immediately**

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `FILEBROWSER_PORT` | 8080 | Web UI port |
| `FILE_ROOT` | /srv | Host directory to browse |
| `PUID` | 1000 | User ID for file permissions |
| `PGID` | 1000 | Group ID for file permissions |

---

## 5. Default Credentials

| Username | Password |
|----------|----------|
| admin | admin |

**Change immediately** after first login via Settings → Profile.

---

## 6. Features

| Feature | Description |
|---------|-------------|
| File Browser | Navigate, upload, download files |
| Multi-user | Separate users with scoped access |
| Editor | Built-in text file editor |
| Sharing | Create shareable download links |
| Search | Quick file search |
| Commands | Execute server-side commands (optional) |

---

## 7. Data Persistence

| Path | Purpose |
|------|---------|
| `./filebrowser.db` | User accounts, settings |
| `./settings.json` | Global configuration |
| `${FILE_ROOT}` | Your actual files |

---

## 8. User Scoping

Create users with restricted directory access:

1. Go to Settings → User Management
2. Add new user
3. Set "Scope" to a subdirectory (e.g., `/srv/photos`)
4. User can only access that directory

---

## 9. Permission Matching

Set `PUID` and `PGID` to match your host user:

```bash
# Find your IDs
id -u  # PUID
id -g  # PGID
```

This ensures files created via FileBrowser have correct ownership.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://filebrowser.org/) | Upstream docs |
| [Storage Solutions](../README.md) | Parent category |
| [Nextcloud AIO](../nextcloud-aio/README.md) | Full-featured alternative |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
