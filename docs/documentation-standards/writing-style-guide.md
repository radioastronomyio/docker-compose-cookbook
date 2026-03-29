<!--
---
title: "Writing Style Guide"
description: "Prose conventions and AI writing tell suppression for all project output"
author: "VintageDon (https://github.com/vintagedon/)"
date: "2026-03-28"
version: "1.0"
status: "Active"
tags:
  - type: guide
  - domain: documentation
related_documents:
  - "[Code Commenting Guide](code-commenting-dual-audience.md)"
  - "[Wikipedia: Signs of AI Writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)"
---
-->

# Writing Style Guide

## 1. Purpose

LLM-generated text has well-documented patterns that trained readers recognize immediately. Since AI agents produce a significant portion of our documentation and code comments, all output (human and AI-assisted) should avoid these patterns. This guide defines the conventions.

These rules are not about hiding AI involvement. They exist because the patterns in question produce worse writing regardless of who or what wrote them.

---

## 2. Scope

This guide applies to all text output across the project: documentation, code comments, commit messages, README files, work logs, and inline prose in configuration files. It supplements the code-commenting guide, which covers AI NOTE conventions specifically.

---

## 3. Punctuation

### Em Dashes

Do not use em dashes. This is the single most recognizable AI writing pattern. Replace them with commas, colons, semicolons, parentheses, or restructure the sentence entirely.

| Instead of | Use |
|-----------|-----|
| `The server runs Ubuntu 24.04 — the LTS release` | `The server runs Ubuntu 24.04, the LTS release` |
| `Three services — Gitea, Semaphore, n8n — run on auto01` | `Three services (Gitea, Semaphore, n8n) run on auto01` |
| `This is the control center — running ML inference and agents` | `This is the control center, running ML inference and agents` |

The rule applies everywhere: prose, table cells, code comments, commit messages.

### Colons and Semicolons

Use colons to introduce lists, explanations, or elaborations. Use semicolons to join related independent clauses. Both are underused in AI output and overused in human-edited AI output trying to avoid em dashes; be deliberate about which you pick.

---

## 4. Sentence Construction

### Negation Parallelism

Avoid "not just X, but Y" and "not X, it's Y" structures. These create theatrical contrast where direct statement works better.

| Instead of | Use |
|-----------|-----|
| `This is not just a monitoring tool, but a complete observability platform` | `This is a complete observability platform` |
| `It's not about speed, it's about reliability` | `Reliability matters more than speed here` |

### Superficial Analysis Clauses

Avoid trailing -ing clauses that add hollow commentary. These clauses typically editorialize without adding information.

| Instead of | Use |
|-----------|-----|
| `The playbook configures sysctl, ensuring consistent hardening` | `The playbook configures sysctl for consistent hardening` |
| `OSQuery runs on every VM, providing baseline telemetry` | `OSQuery runs on every VM for baseline telemetry` |

If the trailing clause adds real information, keep it. If it restates what the main clause already implies, cut it.

---

## 5. Word Choice

### Inflated Significance

Drop words and phrases that editorialize importance. Say what something does; let the reader decide if it matters.

Words to avoid: "pivotal," "watershed," "profound," "rich tapestry," "solidifies," "cornerstone," "game-changing," "transformative."

Phrases to avoid: "serves as a testament," "plays a vital role," "leaves a lasting impact," "underscores the importance," "continues to captivate."

### Editorializing Prefaces

Drop phrases that announce significance before delivering content. Just deliver the content.

Phrases to cut: "it's important to note," "it is worth mentioning," "it bears emphasizing," "no discussion would be complete without," "one cannot overstate."

### Transition Word Crutches

Minimize "moreover," "furthermore," "in addition," "on the other hand," "it is also worth noting." Sentence order and paragraph structure should carry the logical flow without explicit signposting. If you need a transition, prefer shorter ones: "also," "but," "still," "yet."

---

## 6. Structure

### Formulaic Rhythm

Vary sentence length and paragraph structure. AI output tends toward uniform sentence length and identical paragraph openings. Read a section back and check whether every sentence is roughly the same length or every paragraph starts the same way.

### Bold-Title Bullet Lists

Avoid the pattern where every bullet point starts with a bolded keyword followed by a colon and a sentence that restates the keyword. This structure is a strong AI tell and rarely the best way to present information. Use prose, tables, or plain bullets without the bolded-keyword-restatement pattern.

| AI pattern (avoid) | Better alternative |
|----|----|
| **Scalability:** The system is designed to scale easily | The system scales horizontally across nodes |
| **Reliability:** Ensures high availability | Runs active-passive failover with 30s detection |

---

## 7. Applying This Guide

This is guidance for judgment calls, not a compliance checklist. The test for any sentence: would a competent colleague write it this way, or does it read like a chatbot? If the answer is uncertain, rewrite.

These conventions apply to AI-generated output and human-written prose equally. The patterns listed here produce weaker writing regardless of their source.

---

## 8. References

| Resource | Description |
|----------|-------------|
| [Wikipedia: Signs of AI Writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) | Comprehensive catalog of LLM writing patterns |
| [Code Commenting Guide](code-commenting-dual-audience.md) | Companion guide for code comment conventions |
