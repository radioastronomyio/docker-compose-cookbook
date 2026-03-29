<!--
---
title: "Tagging Strategy"
description: "Controlled vocabulary for document classification in docker-compose-cookbook"
author: "VintageDon (https://github.com/vintagedon/)"
date: "2026-03-29"
version: "2.0"
tags:
  - type: guide
  - domain: documentation
related_documents:
  - "[Interior README Template](interior-readme-template.md)"
  - "[General KB Template](general-kb-template.md)"
  - "[Worklog README Template](worklog-readme-template.md)"
---
-->

# Tagging Strategy

## 1. Purpose

Controlled tag vocabulary for the docker-compose-cookbook repository. Consistent tagging enables human navigation and RAG system retrieval.

---

## 2. Why Controlled Vocabulary

Uncontrolled tagging leads to synonyms fragmenting search, inconsistent granularity, and tag proliferation that reduces signal. A controlled vocabulary defines allowed values upfront, ensuring consistency across contributors and time.

---

## 3. Tag Categories

| Category | Question Answered | Required |
|----------|-------------------|----------|
| `type` | What kind of document is this? | Yes |
| `domain` | What subject area? | Yes |
| `status` | What's the lifecycle state? | Recommended |
| `tech` | What technologies involved? | When applicable |

---

## 4. Domain Tags

| Tag | Use For | Boundary |
|-----|---------|----------|
| `ai-ml` | LLM inference, chat UIs, image generation, RAG engines, data annotation | AI and machine learning recipes |
| `automation` | Workflow engines, job schedulers, change detection, social media scheduling | Automation and orchestration recipes |
| `containers` | Container management UIs, update tools, orchestration interfaces | Container management recipes, not the containers themselves |
| `databases` | SQL, NoSQL, vector, graph, time series, wide-column, admin tools | Database recipes across all data models |
| `development` | Git servers, CI/CD pipelines, code editors, dev tools | Development and CI/CD recipes |
| `home-automation` | Smart home, IoT, NVR, home infrastructure | Home automation recipes |
| `media` | Media servers, *Arr stack, photo management, audiobooks | Media and entertainment recipes |
| `messaging` | Push notifications, newsletters, team communication | Messaging and collaboration recipes |
| `monitoring` | Metrics, visualization, log aggregation, status pages, dashboards | Monitoring and logging recipes |
| `networking` | VPNs, DNS, reverse proxies, ad blocking, remote access | Networking recipes |
| `personal` | Knowledge management, productivity, finance, bookmarks, recipes | Personal utility recipes |
| `security` | Authentication, SSO, password vaults, secrets management | Security recipes |
| `storage` | File sync, backup, document management, file sharing | Storage solution recipes |
| `web-apps` | CMS, no-code databases, invoicing, design tools, CRM | Web application server recipes |
| `documentation` | Templates, standards, meta-content about the repo itself | Docs about docs |
| `infrastructure` | Recipe structure, cross-cutting patterns, deployment guides | Repo-level infrastructure concerns |

---

## 5. Type Tags

| Tag | Use For |
|-----|---------|
| `project-root` | Repository root README |
| `directory-readme` | Interior README for any directory |
| `recipe` | Individual Docker Compose recipe documentation |
| `category-readme` | Category-level README indexing recipes |
| `worklog` | Work log entries and milestone documentation |
| `guide` | Step-by-step procedures and how-to documents |
| `reference` | Lookup information: compose patterns, environment variables |

---

## 6. Status Tags

| Tag | Description |
|-----|-------------|
| `draft` | In development, not yet complete |
| `active` | Current, maintained, tested |
| `under-review` | Review in progress |
| `deprecated` | Superseded, avoid for new deployments |
| `archived` | Historical reference only |

---

## 7. Tech Tags

| Tag | Technology |
|-----|-----------|
| `docker` | Docker Engine |
| `compose` | Docker Compose v2 |
| `yaml` | Compose file format |
| `bash` | Shell scripts |
| `python` | Python scripts |
| `postgresql` | PostgreSQL backends |
| `mysql` | MySQL/MariaDB backends |
| `sqlite` | SQLite backends |
| `redis` | Redis backends |
| `nvidia` | GPU-accelerated recipes (NVIDIA Container Toolkit) |

---

## 8. Implementation

### Standard Frontmatter

```yaml
<!--
---
title: "Document Title"
description: "What this document covers"
author: "VintageDon (https://github.com/vintagedon/)"
date: "YYYY-MM-DD"
version: "1.0"
status: "Active"
tags:
  - type: recipe
  - domain: databases
  - tech: [docker, compose, postgresql]
related_documents:
  - "[Related Doc](path/to/doc.md)"
---
-->
```

### Conventions

- Use lowercase, hyphenated values
- Tech tags use canonical names
- One value per line for readability, or array syntax for multi-value
- `related_documents` links use relative paths within the repo

---

## 9. Maintaining the Vocabulary

- This document is the authoritative source for allowed tag values
- Prefer broader tags over proliferating specific ones
- Check for existing coverage before adding new tags
- Backfill existing documents when adding new tags

---

## 10. References

| Resource | Description |
|----------|-------------|
| [Interior README Template](interior-readme-template.md) | Shows tag usage in directory READMEs |
| [General KB Template](general-kb-template.md) | Shows tag usage for standalone docs |
| [Worklog README Template](worklog-readme-template.md) | Shows tag usage for work log entries |
