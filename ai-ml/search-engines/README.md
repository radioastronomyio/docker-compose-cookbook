<!--
---
title: "AI Search Engines"
description: "Docker recipes for AI-powered search and answer synthesis"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: search-engines
---
-->

# AI Search Engines

Docker Compose recipes for AI-powered search engines that aggregate web results and synthesize answers using local LLMs. These replace cloud services like Perplexity AI with sovereign alternatives.

---

## 1. Contents

```
search-engines/
├── perplexica/                # Answer engine with SearXNG integration
└── README.md                  # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [perplexica/](perplexica/README.md) | Web search aggregation with LLM synthesis | ✅ Active |

---

## 3. Architecture Notes

AI search engines combine:

- **Metasearch**: Aggregates results from multiple search providers (SearXNG)
- **LLM Synthesis**: Processes and summarizes results locally
- **Citation**: Provides source attribution for generated answers

These systems keep your search queries private while leveraging web-scale information.

---

## 4. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [LLM Inference](../llm-inference/README.md) | Backend for synthesis |
| [SearXNG](../../networking/searxng/README.md) | Metasearch dependency |
