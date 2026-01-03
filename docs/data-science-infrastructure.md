# Data Infrastructure Reference

This project uses shared research infrastructure on the radioastronomy.io cluster. This document provides connection details and usage patterns.

## VM Inventory

| VMID | Hostname | OS | IP | vCPU | RAM | Storage | Purpose |
|------|----------|----|----|------|-----|---------|---------|
| 2002 | radio-pgsql01 | Ubuntu 24.04 | 10.25.20.8 | 8 | 32G | 250G | Primary research PostgreSQL (pgvector, postgis) |
| 2012 | radio-pgsql02 | Ubuntu 24.04 | 10.25.20.16 | 4 | 16G | 100G | Application PostgreSQL (Gitea, local apps) |
| 2005 | radio-gpu01 | Ubuntu 24.04 | 10.25.20.10 | 12 | 48G | 100G | Data science / ML VM (A4000 GPU) |
| 2018 | radio-neo4j01 | Ubuntu 24.04 | 10.25.20.21 | 6 | 24G | 250G | Graph database |
| 2016 | radio-mongo01 | Ubuntu 24.04 | 10.25.20.18 | 2 | 4G | 100G | Document database (available, unused) |
| 2003 | radio-dfdb01 | Ubuntu 24.04 | 10.25.20.23 | 4 | 8G | — | DragonFlyDB |
| 2011 | radio-fs02 | Server 2025 | 10.25.20.15 | 4 | 6G | 125G | Windows SMB (ML data shares, DESIVAST parquets) |
| 2007 | radio-fs01 | Ubuntu 24.04 | 10.25.20.11 | 2 | 6G | 1TB | NFS server (available, unused) |
| 3001 | radio-k8s01 | Ubuntu 24.04 | 10.25.20.4 | 12 | 48G | 1TB | Kubernetes primary node |
| 2006 | radio-agents01 | Ubuntu 24.04 | 10.25.20.20 | 8 | 32G | 200G | AI agents, MetaMCP, monitoring stack |

## Global Environment

All research VMs source credentials from `/opt/global-env/research.env`. Projects should load this file rather than hardcoding connection details.

```bash
# Load in shell
set -a && source /opt/global-env/research.env && set +a

# Load in Python
from dotenv import load_dotenv
load_dotenv('/opt/global-env/research.env')
```

## Database Connections

### PostgreSQL (pgsql01 - Research Data)

Use admin credentials for all connections. Individual database users deprecated.

```python
import os
import psycopg2

conn = psycopg2.connect(
    host=os.getenv('PGSQL01_HOST'),
    port=os.getenv('PGSQL01_PORT'),
    user=os.getenv('PGSQL01_ADMIN_USER'),
    password=os.getenv('PGSQL01_ADMIN_PASSWORD'),
    database=os.getenv('PGSQL01_DESIVAST_DB')  # or other DB variable
)
```

Available databases on pgsql01:

- `PGSQL01_DESIVAST_DB` — DESI-VAST void catalog
- `PGSQL01_FASTSPEC_DB` — FastSpecFit spectroscopic data
- `PGSQL01_COSMICVOIDS_ARD_DB` — Cosmic voids analysis-ready dataset
- `PGSQL01_RBH1_DB` — RBH-1 validation data

### Neo4j

```python
from neo4j import GraphDatabase

driver = GraphDatabase.driver(
    f"bolt://{os.getenv('NEO4J_HOST')}:{os.getenv('NEO4J_PORT')}",
    auth=(os.getenv('NEO4J_USER'), os.getenv('NEO4J_PASSWORD'))
)
```

### GPU Processing

SSH access for remote execution or use Ollama endpoint directly:

```python
import requests

response = requests.post(
    f"{os.getenv('OLLAMA_ENDPOINT')}/api/generate",
    json={"model": "llama3", "prompt": "..."}
)
```

## Processing Patterns

Default batch processing configuration from env:

- `BATCH_SIZE=10000` — Records per batch
- `MAX_WORKERS=4` — Parallel workers
- `ML_PROCESSING_MODE=remote_gpu` — Offload ML to gpu01

## Monitoring

Logs and metrics from all data science VMs route to radio-agents01's monitoring stack (Prometheus/Loki/Grafana) with 7-day retention.
