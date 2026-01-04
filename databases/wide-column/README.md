<!--
---
title: "Wide-Column Stores"
description: "Distributed databases optimized for large-scale columnar data"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
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
├── cassandra/    # Apache Cassandra
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [cassandra/](cassandra/README.md) | Apache Cassandra - distributed wide-column store | ✅ Active |

---

## 3. Recipe Count: 1

---

## 4. Use Cases

| Use Case | Why Cassandra? |
|----------|----------------|
| Time series at scale | Optimized for write-heavy workloads |
| IoT data | Handles high-velocity sensor data |
| Messaging | Distributed, always-on architecture |
| Multi-datacenter | Built-in replication across regions |

---

## 5. Architecture Notes

Cassandra uses a peer-to-peer architecture with no single point of failure:

- **Partitioning**: Data distributed across nodes via consistent hashing
- **Replication**: Configurable replication factor per keyspace
- **Consistency**: Tunable consistency levels per query
- **CQL**: SQL-like query language

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [timeseries/](../timeseries/README.md) | Alternative for time series |
