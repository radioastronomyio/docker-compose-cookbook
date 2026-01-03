<!--
---
title: "Wide-Column Stores"
description: "Distributed databases optimized for large-scale columnar data"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: wide-column
---
-->

# Wide-Column Stores

Distributed databases that store data in column families, optimized for large-scale read/write workloads across many nodes. These databases offer high availability and horizontal scalability for massive datasets.

---

## 1. Contents

```
wide-column/
├── cassandra/          # Apache Cassandra
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [cassandra/](cassandra/README.md) | Apache Cassandra - distributed wide-column store | ✅ Active |

---

## 3. Use Cases

| Database | Best For |
|----------|----------|
| Cassandra | Time series at scale, IoT, messaging, distributed workloads requiring high availability |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
