<!--
---
title: "Time Series Databases"
description: "Databases optimized for time-stamped data and metrics"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: databases
  - subcategory: timeseries
---
-->

# Time Series Databases

Databases optimized for storing and querying time-stamped data. These databases excel at metrics collection, IoT sensor data, financial data, and monitoring/observability workloads.

---

## 1. Contents

```
timeseries/
├── influxdb/           # InfluxDB time series database
├── questdb/            # QuestDB (planned)
└── README.md           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [influxdb/](influxdb/README.md) | InfluxDB - purpose-built time series database | ✅ Active |
| [questdb/](questdb/) | QuestDB - high-performance SQL time series | 📋 Planned |

---

## 3. Use Cases

| Database | Best For |
|----------|----------|
| InfluxDB | Metrics, monitoring, IoT, real-time analytics |
| QuestDB | High-ingestion workloads, SQL-native time series |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [monitoring-logging/](../../monitoring-logging/README.md) | Often paired with Grafana |
