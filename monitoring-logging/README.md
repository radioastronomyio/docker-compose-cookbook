<!--
---
title: "Monitoring & Logging"
description: "Observability, metrics collection, and log aggregation tools"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: monitoring-logging
---
-->

# Monitoring & Logging

Docker Compose recipes for observability infrastructure including metrics collection, visualization, log aggregation, and alerting systems.

---

## 1. Contents

```
monitoring-logging/
├── cacti-mysql/                        # Cacti network graphing
├── fluentd/                            # Log collector
├── grafana/                            # Visualization dashboards
├── graylog-elasticsearch-mongodb/      # Log management platform
├── Prometheus/                         # Metrics and alerting
└── README.md                           # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [cacti-mysql/](cacti-mysql/README.md) | Cacti - network graphing and monitoring | ✅ Active |
| [fluentd/](fluentd/README.md) | Fluentd - unified logging layer | ✅ Active |
| [grafana/](grafana/README.md) | Grafana - metrics visualization | ✅ Active |
| [graylog-elasticsearch-mongodb/](graylog-elasticsearch-mongodb/README.md) | Graylog - log management | ✅ Active |
| [Prometheus/](Prometheus/README.md) | Prometheus - metrics and alerting | ✅ Active |

---

## 3. Stack Patterns

| Pattern | Components | Use Case |
|---------|------------|----------|
| Metrics Stack | Prometheus + Grafana | Infrastructure monitoring |
| Log Stack | Fluentd + Graylog | Centralized logging |
| Full Observability | Prometheus + Grafana + Fluentd | Complete visibility |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/timeseries/](../databases/timeseries/README.md) | InfluxDB as metrics store |
