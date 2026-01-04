<!--
---
title: "Messaging & Collaboration"
description: "Push notifications, newsletters, and team communication"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: messaging-collaboration
---
-->

# Messaging & Collaboration

Docker Compose recipes for push notifications, newsletter management, and team communication tools.

---

## 1. Contents

```
messaging-collaboration/
├── ntfy/        # Push notification server
├── listmonk/    # Newsletter manager
└── README.md    # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [ntfy](ntfy/README.md) | Push notification server | Script/service alerts |
| [listmonk](listmonk/README.md) | Newsletter and mailing list manager | Email campaigns |

---

## 3. Recipe Count: 2

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Push notifications to phone | Ntfy |
| Newsletter/mailing lists | Listmonk |
| Script completion alerts | Ntfy |
| Subscriber management | Listmonk |

---

## 5. Ntfy Integration Examples

Ntfy provides a simple HTTP API for sending notifications:

```bash
# Simple notification
curl -d "Backup completed" http://localhost:8090/mytopic

# With priority and title
curl -H "Title: Backup Status" -H "Priority: high" \
     -d "Backup completed successfully" http://localhost:8090/mytopic
```

Common integrations:
- Duplicati backup completion
- Watchtower container updates
- Uptime Kuma status changes
- Cron job alerts

---

## 6. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| matrix-synapse | Decentralized chat | Medium |
| mattermost | Team collaboration | Medium |
| rocketchat | Team chat platform | Low |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [monitoring-logging/](../monitoring-logging/README.md) | Alert sources |
| [automation-orchestration/](../automation-orchestration/README.md) | Workflow notifications |
