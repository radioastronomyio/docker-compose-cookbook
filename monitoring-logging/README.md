<!--
---
title: "Monitoring & Logging"
description: "Metrics, visualization, log aggregation, and system observability"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: monitoring-logging
---
-->

# Monitoring & Logging

Docker Compose recipes for metrics collection, visualization, log aggregation, uptime monitoring, and system observability.

---

## 1. Contents

```
monitoring-logging/
├── Prometheus/                        # Time series metrics
├── grafana/                           # Visualization dashboards
├── graylog-elasticsearch-mongodb/     # Log management
├── fluentd/                           # Log aggregation
├── cacti-mysql/                       # Network graphing
├── uptime-kuma/                       # Status monitoring
├── beszel/                            # Lightweight server monitoring
├── glitchtip/                         # Error tracking
├── homarr/                            # Service dashboard
├── scrutiny/                          # Drive S.M.A.R.T. monitoring
├── netdata/                           # Real-time performance
├── dozzle/                            # Container log viewer
├── matomo/                            # Web analytics
└── README.md                          # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [Prometheus](Prometheus/README.md) | Time series metrics database | Metrics collection |
| [grafana](grafana/README.md) | Metrics visualization dashboards | Data visualization |
| [graylog-elasticsearch-mongodb](graylog-elasticsearch-mongodb/README.md) | Centralized log management | Log aggregation |
| [fluentd](fluentd/README.md) | Unified logging layer | Log routing |
| [cacti-mysql](cacti-mysql/README.md) | Network graphing with RRDtool | SNMP monitoring |
| [uptime-kuma](uptime-kuma/README.md) | Status and uptime monitoring | Service health checks |
| [beszel](beszel/README.md) | Lightweight server monitoring | Simple host metrics |
| [glitchtip](glitchtip/README.md) | Error tracking (Sentry alternative) | Application errors |
| [homarr](homarr/README.md) | Dashboard for self-hosted services | Service discovery |
| [scrutiny](scrutiny/README.md) | Hard drive S.M.A.R.T. monitoring | Disk health |
| [netdata](netdata/README.md) | Real-time performance monitoring | Live system metrics |
| [dozzle](dozzle/README.md) | Real-time container log viewer | Container debugging |
| [matomo](matomo/README.md) | Web analytics (GA alternative) | Website traffic |

---

## 3. Recipe Count: 13

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Metrics collection | Prometheus |
| Metrics visualization | Grafana |
| Log aggregation | Graylog or Fluentd |
| Uptime monitoring | Uptime Kuma |
| Real-time system metrics | Netdata |
| Container logs | Dozzle |
| Drive health | Scrutiny |
| Error tracking | GlitchTip |
| Service dashboard | Homarr |
| Web analytics | Matomo |

---

## 5. Observability Stack

A complete observability stack typically includes:

```
                    ┌─────────────┐
                    │   Grafana   │  (Visualization)
                    └──────┬──────┘
                           │
         ┌─────────────────┼─────────────────┐
         │                 │                 │
    ┌────▼────┐      ┌─────▼─────┐     ┌─────▼─────┐
    │Prometheus│      │  Graylog  │     │ GlitchTip │
    │ (metrics)│      │  (logs)   │     │ (errors)  │
    └─────────┘      └───────────┘     └───────────┘
```

---

## 6. Resource Considerations

| Recipe | Resource Usage | Notes |
|--------|---------------|-------|
| Netdata | Low | Real-time, 1-second resolution |
| Dozzle | Minimal | Stateless log streaming |
| Uptime Kuma | Low | SQLite-based |
| Prometheus | Medium | Retention-dependent |
| Grafana | Medium | Dashboard complexity-dependent |
| Graylog | High | Elasticsearch backend |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/timeseries/](../databases/timeseries/README.md) | Metrics storage |
| [messaging-collaboration/](../messaging-collaboration/README.md) | Alert delivery (Ntfy) |
| [container-management/](../container-management/README.md) | Container orchestration |
