<!--
---
title: "Key-Value Stores"
description: "High-performance key-value data stores for caching and sessions"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: key-value
---
-->

# Key-Value Stores

High-performance key-value data stores optimized for speed. These databases excel at caching, session management, real-time analytics, and pub/sub messaging.

---

## 1. Contents

```
key-value/
├── redis/              # Redis in-memory data store
├── dragonfly/          # DragonFly (planned)
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [redis/](redis/README.md) | Redis - in-memory data structure store | ✅ Active |
| [dragonfly/](dragonfly/) | DragonFly - Redis-compatible, higher performance | 📋 Planned |

---

## 3. Use Cases

| Database | Best For |
|----------|----------|
| Redis | Caching, sessions, queues, pub/sub, leaderboards |
| DragonFly | Redis replacement with better memory efficiency and throughput |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [management/](../management/README.md) | Admin tools (redis-commander) |
