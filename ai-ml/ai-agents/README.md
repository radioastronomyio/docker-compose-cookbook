<!--
---
title: "AI Agents"
description: "Docker recipes for autonomous AI agents and coding assistants"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: ai-agents
---
-->

# AI Agents

Docker Compose recipes for autonomous AI agents capable of executing tasks, running code, and interacting with external systems. These go beyond chat interfaces to perform real work.

---

## 1. Contents

```
ai-agents/
├── openhands/                 # Autonomous software engineering agent
└── README.md                  # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [openhands/](openhands/README.md) | Autonomous coding agent with sandbox execution | ✅ Active |

---

## 3. Security Considerations

AI agents require elevated privileges to perform tasks:

- **Docker Socket Access**: Required for sandbox container creation
- **Filesystem Access**: Agents write to mounted workspace directories
- **Network Access**: Some agents browse the web or make API calls

**Never expose these services directly to the internet.** Run behind VPN or strict firewall rules.

---

## 4. Architecture Notes

Agentic systems typically use:

- **Sandbox Containers**: Isolated environments for code execution
- **Tool Calling**: LLM-driven function execution
- **Memory/State**: Persistent context across task iterations

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [LLM Inference](../llm-inference/README.md) | Backend reasoning engine |
| [Automation & Orchestration](../../automation-orchestration/README.md) | Workflow alternatives |
