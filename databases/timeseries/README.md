<!--
---
title: "Time Series Databases"
description: "Databases optimized for time-stamped data and metrics"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
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
├── influxdb/     # InfluxDB time series database
├── questdb/      # QuestDB high-performance TSDB
└── README.md     # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [influxdb/](influxdb/README.md) | InfluxDB - purpose-built time series database | ✅ Active |
| [questdb/](questdb/README.md) | QuestDB - high-performance SQL time series | ✅ Active |

---

## 3. Recipe Count: 2

---

## 4. Selection Guide

| Database | Best For |
|----------|----------|
| InfluxDB | Metrics, monitoring, IoT, real-time analytics |
| QuestDB | High-ingestion workloads, SQL-native time series |

---

## 5. Comparison

| Feature | InfluxDB | QuestDB |
|---------|----------|---------|
| Query language | Flux / InfluxQL | PostgreSQL-compatible SQL |
| Ingestion speed | High | Very High |
| Grafana integration | Native | Native |
| Learning curve | Medium | Low (SQL) |

---

## 6. Related

| Document | Relationship |
|----------|--------------|
| [databases/](../README.md) | Parent category |
| [monitoring-logging/](../../monitoring-logging/README.md) | Grafana visualization |
| [monitoring-logging/Prometheus/](../../monitoring-logging/Prometheus/README.md) | Alternative metrics storage |
