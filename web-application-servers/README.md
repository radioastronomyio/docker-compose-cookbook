<!--
---
title: "Web Application Servers"
description: "CMS platforms, no-code databases, and business applications"
author: "VintageDon"
date: "2025-01-04"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - category: web-application-servers
---
-->

# Web Application Servers

Docker Compose recipes for content management systems, no-code databases, design platforms, and business applications.

---

## 1. Contents

```
web-application-servers/
├── ghost/          # Publishing platform
├── baserow/        # No-code database
├── invoice-ninja/  # Invoicing and billing
├── docmost/        # Documentation platform
├── penpot/         # Design platform
├── twenty/         # CRM platform
└── README.md       # This file
```

---

## 2. Recipes

| Recipe | Description | Use Case |
|--------|-------------|----------|
| [ghost](ghost/README.md) | Professional publishing platform | Blogging, newsletters |
| [baserow](baserow/README.md) | No-code database (Airtable alternative) | Spreadsheet databases |
| [invoice-ninja](invoice-ninja/README.md) | Invoicing and billing platform | Freelancer/SMB billing |
| [docmost](docmost/README.md) | Documentation and wiki platform | Team documentation |
| [penpot](penpot/README.md) | Open-source design platform | Figma alternative |
| [twenty](twenty/README.md) | Modern CRM platform | Customer relationship management |

---

## 3. Recipe Count: 6

---

## 4. Quick Reference

| Need | Recommended |
|------|-------------|
| Blog/publishing | Ghost |
| Spreadsheet database | Baserow |
| Invoicing | Invoice Ninja |
| Team documentation | Docmost |
| UI/UX design | Penpot |
| CRM | Twenty |

---

## 5. Platform Comparison

| Platform | Alternative To | Key Strength |
|----------|---------------|--------------|
| Ghost | Medium, Substack | Clean writing experience |
| Baserow | Airtable | API-first, self-hosted |
| Invoice Ninja | FreshBooks, QuickBooks | Full invoicing suite |
| Docmost | Notion, Confluence | Collaborative docs |
| Penpot | Figma | Open-source design |
| Twenty | Salesforce, HubSpot | Modern, extensible CRM |

---

## 6. Critical Configuration Notes

### URL Configuration

Most platforms in this category are strict about URL settings:

| Platform | Variable | Impact if Wrong |
|----------|----------|-----------------|
| Ghost | `url` | Infinite redirects, broken assets |
| Baserow | `BASEROW_PUBLIC_URL` | CORS failures, API errors |
| Invoice Ninja | `APP_URL` | Redirect loops |

Always verify the URL matches your actual access method (http vs https, domain, port).

### APP_KEY Generation

Invoice Ninja requires a pre-generated encryption key:
```bash
docker run --rm -it invoiceninja/invoiceninja php artisan key:generate --show
```

---

## 7. Integration Patterns

### Content + Analytics
```
Ghost (blog) → Matomo (analytics) → Listmonk (newsletter)
```

### Business Operations
```
Twenty (CRM) → Invoice Ninja (billing) → Firefly III (accounting)
```

---

## 8. Related

| Document | Relationship |
|----------|--------------|
| [Repository Root](../README.md) | Parent directory |
| [personal-utilities/](../personal-utilities/README.md) | BookStack for wikis |
| [monitoring-logging/](../monitoring-logging/README.md) | Matomo for analytics |
| [messaging-collaboration/](../messaging-collaboration/README.md) | Listmonk for newsletters |
| [automation-orchestration/](../automation-orchestration/README.md) | n8n for workflows |
