<!--
---
title: "Media & Entertainment"
description: "Media servers, streaming, and content management"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: media-entertainment
---
-->

# Media & Entertainment

Docker Compose recipes for media servers, streaming platforms, photo management, and the complete *Arr media automation stack.

---

## 1. Contents

```
media-entertainment/
├── jellyfin/        # Open-source media server
├── prowlarr/        # Indexer manager
├── sonarr/          # TV series automation
├── radarr/          # Movie automation
├── jellyseerr/      # Media request management
├── bazarr/          # Subtitle automation
├── immich/          # Photo management
├── audiobookshelf/  # Audiobook server
└── README.md        # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [jellyfin](jellyfin/README.md) | Open-source media server with GPU transcoding | Stream movies/TV |
| [prowlarr](prowlarr/README.md) | Indexer manager for *Arr stack | Centralized indexer config |
| [sonarr](sonarr/README.md) | TV series lifecycle management | Automated TV downloads |
| [radarr](radarr/README.md) | Movie lifecycle management | Automated movie downloads |
| [jellyseerr](jellyseerr/README.md) | Media request management UI | User content requests |
| [bazarr](bazarr/README.md) | Subtitle automation | Auto-download subtitles |
| [immich](immich/README.md) | Self-hosted Google Photos alternative | Photo backup/management |
| [audiobookshelf](audiobookshelf/README.md) | Audiobook and podcast server | Audio content library |

---

## 3. Recipe Count: 8

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Free media server | Jellyfin |
| Automated TV downloads | Sonarr + Prowlarr |
| Automated movie downloads | Radarr + Prowlarr |
| User media requests | Jellyseerr |
| Subtitle management | Bazarr |
| Photo backup | Immich |
| Audiobooks/podcasts | Audiobookshelf |

---

## 5. *Arr Stack Architecture

The *Arr applications work together for automated media management:

```
Prowlarr (indexers)
    ↓
Sonarr (TV) / Radarr (Movies)
    ↓
Download Client (qBittorrent, SABnzbd)
    ↓
Jellyfin (streaming) ← Bazarr (subtitles)
    ↑
Jellyseerr (requests)
```

### Atomic Moves Strategy

For optimal I/O performance, mount a unified `/data` volume containing both downloads and media library. This enables hardlinks instead of copy operations.

---

## 6. Hardware Acceleration

Jellyfin supports GPU transcoding for real-time format conversion:

| GPU | Capability |
|-----|------------|
| NVIDIA (NVENC) | Best performance, recommended |
| Intel QuickSync | Good, integrated GPUs |
| AMD VCE | Supported |

Configure via `NVIDIA_DRIVER_CAPABILITIES=compute,video,utility` to share GPU with AI workloads.

---

## 7. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [storage-solutions/](../storage-solutions/README.md) | Media storage backends |
| [networking/](../networking/README.md) | VPN for downloads |
| [ai-ml/](../ai-ml/README.md) | Shares GPU resources |
