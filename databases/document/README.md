<!--
---
title: "Document Databases"
description: "NoSQL document-oriented databases storing JSON-like documents"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: document
---
-->

# Document Databases

NoSQL document-oriented databases that store data as JSON-like documents. These databases offer flexible schemas and are well-suited for hierarchical data, content management, and applications with evolving data models.

---

## 1. Contents

```
document/
├── mongodb/      # MongoDB document store
├── couchdb/      # Apache CouchDB
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [mongodb/](mongodb/README.md) | MongoDB - leading document database | ✅ Active |
| [couchdb/](couchdb/README.md) | CouchDB - HTTP API with MVCC | ✅ Active |

---

## 3. Recipe Count: 2

---

## 4. Selection Guide

| Database | Best For |
|----------|----------|
| MongoDB | Content management, catalogs, user profiles, real-time analytics |
| CouchDB | Offline-first apps, replication, HTTP-native access |

---

## 5. Comparison

| Feature | MongoDB | CouchDB |
|---------|---------|---------|
| Query language | MQL | Mango/MapReduce |
| Replication | Replica sets | Multi-master |
| API | Binary protocol | REST/HTTP |
| Offline support | Limited | Built-in |

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [management/](../management/README.md) | Admin tools (Mongo Express) |
