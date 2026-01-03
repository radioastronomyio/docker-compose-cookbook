<!--
---
title: "Media & Entertainment"
description: "Media servers, streaming, and content management"
author: "VintageDon"
date: "2025-01-02"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: media-entertainment
---
-->

# Media & Entertainment

Docker Compose recipes for media servers, streaming platforms, and media library management.

---

## 1. Contents

```
media-entertainment/
└── README.md           # This file
```

---

## 2. Planned Recipes

| Recipe | Description | Priority |
|--------|-------------|----------|
| jellyfin | Open-source media server | High |
| plex | Media server with apps | High |
| sonarr | TV show management | Medium |
| radarr | Movie management | Medium |
| prowlarr | Indexer manager | Medium |
| overseerr | Media request management | Medium |
| tautulli | Plex statistics | Low |

---

## 3. Use Cases

| Need | Recommended |
|------|-------------|
| Free media server | Jellyfin |
| Polished media server | Plex |
| Automated TV downloads | Sonarr |
| Automated movie downloads | Radarr |
| User requests | Overseerr |

---

## 4. *Arr Stack

The *arr applications work together for automated media management:

```
Prowlarr (indexers) → Sonarr/Radarr (management) → Download Client → Jellyfin/Plex
```

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [storage-solutions/](../storage-solutions/README.md) | Media storage |
| [networking/](../networking/README.md) | VPN for downloads |
