<!--
---
title: "Storage Solutions"
description: "File sync, backup, document management, and cloud storage"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: storage-solutions
---
-->

# Storage Solutions

Docker Compose recipes for file synchronization, backup tools, document management, and self-hosted cloud storage.

---

## 1. Contents

```
storage-solutions/
├── nextcloud-aio/    # Self-hosted cloud storage
├── paperless-ngx/    # Document management
├── filebrowser/      # Web file manager
├── pingvin-share/    # File sharing (WeTransfer alternative)
├── syncthing/        # Decentralized file sync
├── duplicati/        # Encrypted backup
└── README.md         # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [nextcloud-aio](nextcloud-aio/README.md) | Self-hosted cloud storage platform | Google Drive/Dropbox alternative |
| [paperless-ngx](paperless-ngx/README.md) | Document management with OCR | Paperless office |
| [filebrowser](filebrowser/README.md) | Web-based file manager | Simple file access |
| [pingvin-share](pingvin-share/README.md) | File sharing with expiring links | WeTransfer alternative |
| [syncthing](syncthing/README.md) | Decentralized file synchronization | Cross-device sync |
| [duplicati](duplicati/README.md) | Encrypted backup to cloud/local | Disaster recovery |

---

## 3. Recipe Count: 6

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Full cloud suite (files, calendar, contacts) | Nextcloud AIO |
| Document scanning/OCR | Paperless-ngx |
| Simple web file manager | FileBrowser |
| Send large files to others | Pingvin Share |
| Sync files across devices | Syncthing |
| Encrypted backups | Duplicati |

---

## 5. Use Case Matrix

| Tool | Sync | Share | Backup | DMS |
|------|------|-------|--------|-----|
| Nextcloud | ✅ | ✅ | ✅ | Partial |
| Paperless-ngx | ❌ | ❌ | ❌ | ✅ |
| FileBrowser | ❌ | ✅ | ❌ | ❌ |
| Pingvin Share | ❌ | ✅ | ❌ | ❌ |
| Syncthing | ✅ | ❌ | ❌ | ❌ |
| Duplicati | ❌ | ❌ | ✅ | ❌ |

---

## 6. Backup Strategy (3-2-1 Rule)

Duplicati enables the 3-2-1 backup rule:
- **3** copies of data
- **2** different media types
- **1** offsite location

Supported destinations: S3, Backblaze B2, Google Drive, SFTP, local NAS.

---

## 7. Syncthing Architecture

Syncthing creates a decentralized mesh — no central server:

```
Desktop ←──→ Laptop
    ↕           ↕
 Phone ←──→ Server
```

Data travels directly between devices via NAT traversal.

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [media-entertainment/](../media-entertainment/README.md) | Media library storage |
| [personal-utilities/](../personal-utilities/README.md) | Knowledge management |
| [messaging-collaboration/](../messaging-collaboration/README.md) | Backup notifications (Ntfy) |
