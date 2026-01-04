<!--
---
title: "Audiobookshelf Docker Setup"
description: "Docker Compose deployment for Audiobookshelf audiobook server"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - category: media-entertainment
  - tech: audiobookshelf
related_documents:
  - "[Media & Entertainment README](../README.md)"
  - "[Official Docs](https://www.audiobookshelf.org/docs)"
---
-->

# Audiobookshelf Docker Setup

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Audiobookshelf is a self-hosted audiobook and podcast server. It provides streaming playback, progress sync across devices, and podcast management with automatic downloads.

---

## 1. Contents

```
audiobookshelf/
├── docker-compose.yml  # Main compose file
├── .env.example        # Environment template
└── README.md           # This file
```

---

## 2. Prerequisites

- Docker Engine 20.10+
- Docker Compose 2.0+
- Audiobook files (M4B, MP3, etc.)

---

## 3. Quick Start

1. Copy `.env.example` to `.env`
2. Set `AUDIOBOOKS_PATH` to your audiobook directory
3. Run `docker compose up -d`
4. Access UI at `http://localhost:13378`
5. Create admin account
6. Add libraries and scan

---

## 4. Configuration

| Variable | Default | Description |
|----------|---------|-------------|
| `AUDIOBOOKSHELF_PORT` | 13378 | Web UI port |
| `AUDIOBOOKS_PATH` | ./audiobooks | Audiobook directory |
| `PODCASTS_PATH` | ./podcasts | Podcast directory |
| `TZ` | America/New_York | Timezone |

---

## 5. Library Organization

Audiobooks should follow this structure:

```
/audiobooks/
├── Author Name/
│   └── Book Title/
│       ├── cover.jpg (optional)
│       ├── metadata.json (optional)
│       └── audiofile.m4b
```

Audiobookshelf fetches metadata from Audible, Google Books, and other sources automatically.

---

## 6. Supported Formats

| Format | Type |
|--------|------|
| M4B | Audiobook (chapters supported) |
| MP3 | Audio files |
| M4A | AAC audio |
| FLAC | Lossless audio |
| OGG | Vorbis audio |
| OPUS | Opus audio |

---

## 7. Features

| Feature | Description |
|---------|-------------|
| Progress Sync | Track position across devices |
| Chapters | Navigate by chapter markers |
| Sleep Timer | Auto-stop playback |
| Playback Speed | Variable speed adjustment |
| Bookmarks | Mark important sections |
| Collections | Organize books into groups |
| Podcast RSS | Subscribe and auto-download |

---

## 8. Data Persistence

| Path | Purpose |
|------|---------|
| `./config` | User database, settings |
| `./metadata` | Cached metadata, covers |
| `${AUDIOBOOKS_PATH}` | Your audiobook files |
| `${PODCASTS_PATH}` | Downloaded podcast episodes |

Keep metadata separate from media for easier backups.

---

## 9. Mobile Apps

Official apps available:

- iOS: App Store
- Android: Google Play / F-Droid

Apps sync progress and allow offline downloads.

---

## 10. Related

| Resource | Description |
|----------|-------------|
| [Official Documentation](https://www.audiobookshelf.org/docs) | Upstream docs |
| [Media & Entertainment](../README.md) | Parent category |
| [Jellyfin](../jellyfin/README.md) | General media server |

---

## 11. License

This project is licensed under the MIT License - see the [LICENSE](../../LICENSE) file for details.
