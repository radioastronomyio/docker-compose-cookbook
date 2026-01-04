<!--
---
title: "Personal Utilities"
description: "Knowledge management, productivity, and personal finance tools"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: personal-utilities
---
-->

# Personal Utilities

Docker Compose recipes for knowledge management, productivity tools, personal finance, and daily utility applications.

---

## 1. Contents

```
personal-utilities/
├── bookstack/       # Wiki and documentation
├── linkwarden/      # Bookmark manager with archival
├── excalidraw/      # Virtual whiteboard
├── firefly-iii/     # Personal finance manager
├── it-tools/        # Developer utilities
├── hoarder/         # Bookmark and read-later
├── mealie/          # Recipe manager
├── actual-budget/   # Budget tracking
└── README.md        # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [bookstack](bookstack/README.md) | Wiki and documentation platform | Knowledge base |
| [linkwarden](linkwarden/README.md) | Bookmark manager with page archival | Link rot protection |
| [excalidraw](excalidraw/README.md) | Virtual whiteboard for diagrams | Sketching/planning |
| [firefly-iii](firefly-iii/README.md) | Personal finance manager | Expense tracking |
| [it-tools](it-tools/README.md) | Developer utilities collection | JWT, Base64, hashing |
| [hoarder](hoarder/README.md) | Bookmark and read-later app | Content saving |
| [mealie](mealie/README.md) | Recipe manager and meal planner | Cooking organization |
| [actual-budget](actual-budget/README.md) | Budget tracking application | Financial planning |

---

## 3. Recipe Count: 8

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Documentation wiki | BookStack |
| Bookmark archival | Linkwarden |
| Simple bookmarking | Hoarder |
| Whiteboard/diagrams | Excalidraw |
| Personal finance | Firefly III |
| Budget tracking | Actual Budget |
| Developer tools | IT-Tools |
| Recipe management | Mealie |

---

## 5. Knowledge Management Stack

For comprehensive personal knowledge management:

```
Linkwarden (bookmarks/archival)
    ↓
BookStack (organized documentation)
    ↓
Excalidraw (visual diagrams)
```

---

## 6. Finance Stack

For complete personal finance tracking:

| Tool | Purpose |
|------|---------|
| Firefly III | Full double-entry bookkeeping |
| Actual Budget | Envelope budgeting method |

Choose based on preferred methodology — Firefly III for detailed tracking, Actual Budget for envelope-style budgeting.

---

## 7. Security Benefits

IT-Tools provides a "safe harbor" for sensitive operations:
- JWT decoding without exposing tokens to public websites
- Password/hash generation locally
- Base64 encoding of sensitive data

All processing happens client-side within your network.

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [storage-solutions/](../storage-solutions/README.md) | Document storage |
| [web-application-servers/](../web-application-servers/README.md) | CMS platforms |
