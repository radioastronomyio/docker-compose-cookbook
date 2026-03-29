<!--
---
title: "Documentation Standards"
description: "Templates and guidelines for project documentation"
author: "VintageDon (https://github.com/vintagedon/)"
date: "2026-03-28"
version: "2.0"
status: "Active"
tags:
  - type: directory-readme
  - domain: documentation
---
-->

# Documentation Standards

Templates for RAG-optimized documentation. Start lean, expand as needed.

---

## 1. Contents

```
documentation-standards/
├── primary-readme-template.md       # Repository root README
├── interior-readme-template.md      # Directory README
├── general-kb-template.md           # Standalone documents
├── worklog-readme-template.md       # Work log entries
├── code-commenting-dual-audience.md # Code comment methodology
├── writing-style-guide.md           # Prose conventions and AI tell suppression
├── tagging-strategy.md              # Controlled vocabulary for tags
├── script-header-python.md          # Python script header
├── script-header-shell.md           # Bash script header
├── script-header-powershell.md      # PowerShell script header
└── README.md                        # This file
```

---

## 2. Templates

### Document Templates

| Template | Use For |
|----------|---------|
| [primary-readme-template.md](primary-readme-template.md) | Repository root README.md |
| [interior-readme-template.md](interior-readme-template.md) | Any directory that needs a README |
| [general-kb-template.md](general-kb-template.md) | Standalone documents (guides, specs, reports, runbooks) |
| [worklog-readme-template.md](worklog-readme-template.md) | Date-based work log entries in `work-logs/` |

### Script Header Templates

| Template | Use For |
|----------|---------|
| [script-header-python.md](script-header-python.md) | All `.py` files |
| [script-header-shell.md](script-header-shell.md) | All `.sh` files |
| [script-header-powershell.md](script-header-powershell.md) | All `.ps1` files |

### Guidelines

| Document | Use For |
|----------|---------|
| [tagging-strategy.md](tagging-strategy.md) | Controlled vocabulary for YAML frontmatter tags |
| [code-commenting-dual-audience.md](code-commenting-dual-audience.md) | Writing comments for humans and AI agents |
| [writing-style-guide.md](writing-style-guide.md) | Prose conventions, AI tell suppression |

---

## 3. Core Principles

### RAG Infrastructure (Always Keep)

- **YAML frontmatter** enables retrieval and filtering
- **Semantic numbering** provides predictable section structure
- **Preserved gaps** maintain stability: if you omit section 4, keep numbering as 1, 2, 3, 5 (never renumber)

### Bottom-Up Approach

- Start with minimal template
- Add sections as content requires
- Don't fill sections for completeness
- Wrapper is thin; content is the point

---

## 4. Template Selection

### Documents

```
Is it the repository root README?
├─ Yes → primary-readme-template.md
└─ No: Is it a directory README?
        ├─ Yes → interior-readme-template.md
        └─ No: Is it a standalone document?
                └─ Yes → general-kb-template.md
```

### Scripts

```
What language?
├─ Python (.py)     → script-header-python.md
├─ Bash (.sh)       → script-header-shell.md
└─ PowerShell (.ps1)→ script-header-powershell.md
```

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [docs/](../README.md) | Parent directory |
