<!--
---
title: "Storage Solutions"
description: "Object storage, file sync, and backup solutions"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: storage-solutions
---
-->

# Storage Solutions

Docker Compose recipes for object storage, file synchronization, and backup solutions.

---

## 1. Contents

```
storage-solutions/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| minio | S3-compatible object storage | High |
| nextcloud | File sync and collaboration | High |
| seafile | File sync with better performance | Medium |
| syncthing | Peer-to-peer file sync | Medium |
| duplicati | Backup to cloud storage | Medium |
| restic-rest-server | Restic backup repository | Low |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| S3-compatible API | MinIO |
| Dropbox replacement | Nextcloud or Seafile |
| P2P sync without server | Syncthing |
| Encrypted backups | Duplicati or Restic |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/](../databases/README.md) | Backend storage for sync tools |
