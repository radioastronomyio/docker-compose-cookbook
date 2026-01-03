<!--
---
title: "Messaging & Collaboration"
description: "Chat, email, and team communication platforms"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: messaging-collaboration
---
-->

# Messaging & Collaboration

Docker Compose recipes for self-hosted chat, email, and team collaboration platforms.

---

## 1. Contents

```
messaging-collaboration/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| matrix-synapse | Matrix homeserver (federated chat) | High |
| mattermost | Slack alternative | High |
| rocketchat | Team chat platform | Medium |
| element-web | Matrix web client | Medium |
| mailcow | Full mail server stack | Medium |
| mailu | Lightweight mail server | Low |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Federated chat | Matrix (Synapse + Element) |
| Slack replacement | Mattermost |
| Full-featured team chat | Rocket.Chat |
| Self-hosted email | Mailcow or Mailu |

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [databases/](../databases/README.md) | Backend storage |
| [security/](../security/README.md) | SSO integration |
