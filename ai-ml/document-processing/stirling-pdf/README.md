<!--
---
title: "Stirling-PDF"
description: "Self-hosted PDF manipulation toolkit with OCR capabilities"
author: "VintageDon"
tags:
  - type: recipe
  - category: ai-ml/document-processing
  - application: stirling-pdf
---
-->

# Stirling-PDF

Comprehensive self-hosted PDF manipulation toolkit combining standard PDF operations (merge, split, convert) with Tesseract OCR for text recognition from scanned documents.

---

## 1. Overview

Stirling-PDF provides a web interface for common PDF operations without uploading documents to third-party services. The OCR functionality enables text extraction from scanned PDFs and images.

| Attribute | Value |
|-----------|-------|
| **Image** | `stirlingtools/stirling-pdf:latest` |
| **Ports** | 8080 (Web UI) |
| **GPU Required** | No |
| **Documentation** | [github.com/Stirling-Tools/Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF) |

---

## 2. Prerequisites

| Requirement | Details |
|-------------|---------|
| Docker | 20.10+ with Compose V2 |
| Storage | Sufficient for temporary file processing |

---

## 3. Quick Start

```bash
# Clone and navigate
cd ai-ml/document-processing/stirling-pdf

# Configure environment
cp .env.example .env

# Start the service
docker compose up -d

# Access UI
open http://localhost:8080
```

---

## 4. Configuration

### 4.1 Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `DOCKER_ENABLE_SECURITY` | `false` | Enable authentication |
| `SYSTEM_MAXFILESIZE` | `200` | Maximum file size in MB |
| `INSTALL_BOOK_AND_ADVANCED_HTML_OPS` | `false` | Enable calibre/ebook features |

---

## 5. Features

| Category | Operations |
|----------|------------|
| **Merge/Split** | Combine PDFs, extract pages, rearrange |
| **Convert** | PDF to/from images, Word, HTML |
| **OCR** | Text recognition from scanned documents |
| **Security** | Add/remove passwords, permissions |
| **Modify** | Rotate, crop, compress, watermark |

---

## 6. OCR Configuration

### 6.1 Language Packs

Mount additional Tesseract language data for non-English OCR:

```yaml
volumes:
  - ./trainingData:/usr/share/tessdata
```

Download language packs from [tessdata repository](https://github.com/tesseract-ocr/tessdata).

### 6.2 Performance

OCR is CPU-intensive. For large batches:

- Increase container CPU limits
- Process during off-peak hours
- Consider GPU-accelerated alternatives for high volume

---

## 7. Volumes

| Path | Purpose |
|------|---------|
| `./trainingData` | Tesseract language data |
| `./configs` | Application configuration |

---

## 8. Security

For production deployments:

```yaml
environment:
  - DOCKER_ENABLE_SECURITY=true
  - SECURITY_ENABLELOGIN=true
  - SECURITY_INITIALLOGIN_USERNAME=admin
  - SECURITY_INITIALLOGIN_PASSWORD=changeme
```

---

## 9. Related

| Document | Relationship |
|----------|--------------|
| [Document Processing README](../README.md) | Parent category |
| [AI & ML Overview](../../README.md) | Category index |
