<!--
---
title: "Data Annotation"
description: "Docker recipes for data labeling and annotation platforms"
author: "VintageDon"
date: "2025-01-03"
version: "1.0"
status: "Active"
tags:
  - type: directory-readme
  - category: ai-ml
  - subcategory: data-annotation
---
-->

# Data Annotation

Docker Compose recipes for data labeling and annotation platforms. These tools are essential for creating training datasets for machine learning models, RLHF workflows, and quality assurance.

---

## 1. Contents

```
data-annotation/
├── label-studio/              # Universal multi-modal annotation
├── cvat/                      # Computer vision specialization
└── README.md                  # This file
```

---

## 2. Recipes

| Recipe | Description | Status |
|--------|-------------|--------|
| [label-studio/](label-studio/README.md) | Multi-modal annotation (text, image, audio, video) | ✅ Active |
| [cvat/](cvat/README.md) | Computer vision with video interpolation and 3D | ✅ Active |

---

## 3. Selection Guide

| Use Case | Recommended |
|----------|-------------|
| Text classification, NER, sentiment | Label Studio |
| Multi-modal projects (mixed data types) | Label Studio |
| Video object tracking | CVAT |
| 3D point cloud annotation | CVAT |
| Large-scale image segmentation | CVAT |

---

## 4. MLOps Integration

Both platforms support:

- **ML Backends**: Pre-labeling with model predictions
- **Webhooks**: Trigger pipelines on annotation completion
- **Export Formats**: COCO, YOLO, Pascal VOC, custom JSON

---

## 5. Related

| Document | Relationship |
|----------|--------------|
| [AI & ML](../README.md) | Parent directory |
| [Image Generation](../image-generation/README.md) | Synthetic data creation |
| [LLM Inference](../llm-inference/README.md) | Text pre-labeling backends |
