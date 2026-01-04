<!--
---
title: "Home Automation"
description: "Smart home platforms, IoT, and home infrastructure"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: home-automation
---
-->

# Home Automation

Docker Compose recipes for smart home platforms, IoT infrastructure, and home automation tools.

---

## 1. Contents

```
home-automation/
├── frigate/        # AI-powered NVR
└── README.md       # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [frigate](frigate/README.md) | AI-powered NVR with object detection | Security cameras with ML |

---

## 3. Recipe Count: 1

---

## 4. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| home-assistant | Smart home hub | High |
| node-red | Flow-based automation | Medium |
| mosquitto | MQTT broker | Medium |
| zigbee2mqtt | Zigbee to MQTT bridge | Medium |
| esphome | ESP device firmware | Low |

---

## 5. Quick Reference

| Need | Recommended |
|------|-------------|
| Security cameras with AI | Frigate |
| Central smart home hub | Home Assistant (planned) |
| Custom automations | Node-RED (planned) |
| IoT device communication | Mosquitto MQTT (planned) |

---

## 6. Frigate Hardware Requirements

Frigate benefits significantly from hardware acceleration:

| Hardware | Purpose |
|----------|---------|
| NVIDIA GPU | Object detection (recommended) |
| Google Coral | Efficient TPU inference |
| Intel QuickSync | Video decoding |

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [ai-ml/](../ai-ml/README.md) | AI/ML backends |
| [networking/](../networking/README.md) | Network infrastructure |
| [monitoring-logging/](../monitoring-logging/README.md) | System monitoring |
