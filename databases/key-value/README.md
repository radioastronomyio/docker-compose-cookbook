<!--
---
title: "Key-Value Stores"
description: "High-performance key-value data stores for caching and sessions"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
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
├── redis/        # Redis in-memory data store
├── dragonfly/    # DragonFly Redis alternative
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [redis/](redis/README.md) | Redis - in-memory data structure store | ✅ Active |
| [dragonfly/](dragonfly/README.md) | DragonFly - Redis-compatible with higher performance | ✅ Active |

---

## 3. Recipe Count: 2

---

## 4. Selection Guide

| Database | Best For |
|----------|----------|
| Redis | Caching, sessions, queues, pub/sub, leaderboards |
| Dragonfly | Redis replacement with better memory efficiency and throughput |

---

## 5. Comparison

| Feature | Redis | Dragonfly |
|---------|-------|-----------|
| Protocol | Redis | Redis-compatible |
| Multi-threading | Single + I/O | Fully multi-threaded |
| Memory efficiency | Good | Better |
| Drop-in replacement | N/A | ✅ |

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [management/](../management/README.md) | Admin tools (Redis Commander) |
