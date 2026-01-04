# Docker Compose Cookbook Architecture

## Overview

The Docker Compose Cookbook is architected as a flat collection of categorized recipes, each self-contained with everything needed for deployment. The structure prioritizes discoverability (categories), self-sufficiency (each recipe works standalone), and consistency (standardized templates).

The architecture follows the Interior README Pattern - every directory contains a README that describes its contents and links to child directories. This enables both human navigation and AI agent comprehension of the repository structure.

## Core Components

### Category Directories
**Purpose:** Group related recipes by service type  
**Location:** Root level (e.g., `databases/`, `networking/`, `ai-ml/`)  
**Key Characteristics:** Contains subcategories or recipe directories, has an interior README documenting all recipes within

### Recipe Directories
**Purpose:** Self-contained deployment configurations for a single service  
**Location:** Within category directories (e.g., `databases/relational/mysql/`)  
**Key Characteristics:** docker-compose.yml, .env.example, README.md, optional docs/ folder

### Documentation Standards
**Purpose:** Templates ensuring consistent documentation across all recipes  
**Location:** `docs/documentation-standards/`  
**Key Characteristics:** Interior README template, recipe README template, tagging strategy

## Structure

```
docker-compose-cookbook/
├── ai-ml/
│   ├── llm-inference/        # Ollama, LocalAI, vLLM, Text-Gen-WebUI
│   ├── chat-interfaces/      # Open WebUI, LibreChat, AnythingLLM, PrivateGPT
│   ├── image-generation/     # Automatic1111, ComfyUI, Fooocus, InvokeAI, SwarmUI
│   ├── audio-intelligence/   # Faster Whisper, Wyoming Whisper
│   ├── document-processing/  # Stirling-PDF
│   ├── rag-engines/          # RAGFlow
│   ├── search-engines/       # Perplexica
│   ├── ai-agents/            # OpenHands
│   ├── data-annotation/      # Label Studio, CVAT
│   └── README.md
├── automation-orchestration/ # n8n, Flowise, Dify, AWX, Rundeck, StackStorm, etc.
├── container-management/     # Portainer, Dockge, Watchtower
├── databases/
│   ├── relational/           # MySQL, MariaDB, PostgreSQL, SQLite
│   ├── document/             # MongoDB, CouchDB
│   ├── key-value/            # Redis, Dragonfly
│   ├── graph/                # Neo4j
│   ├── timeseries/           # InfluxDB, QuestDB
│   ├── vector/               # Qdrant, Milvus, Weaviate, ChromaDB
│   ├── wide-column/          # Cassandra
│   ├── management/           # phpMyAdmin, pgAdmin, Redis Commander, Mongo Express
│   └── README.md
├── development-ci-cd/        # Gitea, GitLab CE, Gogs, Jenkins, Code-Server
├── home-automation/          # Frigate
├── media-entertainment/      # Jellyfin, *Arr stack, Immich, Audiobookshelf
├── messaging-collaboration/  # Ntfy, Listmonk
├── monitoring-logging/       # Prometheus, Grafana, Graylog, Uptime Kuma, etc.
├── networking/               # Traefik, NPM, WireGuard, Pi-hole, Guacamole, etc.
├── personal-utilities/       # BookStack, Firefly III, Mealie, IT-Tools, etc.
├── security/                 # Authentik, Vaultwarden
├── storage-solutions/        # Nextcloud, Paperless-ngx, Syncthing, Duplicati, etc.
├── web-application-servers/  # Ghost, Baserow, Invoice Ninja, Penpot, etc.
├── docs/
│   └── documentation-standards/
├── skeleton/                 # Template for new recipes
├── work-logs/                # Development phases
└── README.md                 # Repository root
```

## Design Patterns and Principles

### Key Patterns

- **Interior README Pattern:** Every directory self-documents via README with tree structure and child links
- **Self-Contained Recipes:** Each recipe works independently without external dependencies
- **Three-File Recipe Structure:** README.md, docker-compose.yml, .env.example as the standard pattern
- **Environment Separation:** All configuration via .env files, never hardcoded

### Design Principles

1. **Clone and Deploy:** Minimize steps from clone to running service
2. **Consistency Over Cleverness:** Same structure everywhere, even if slightly redundant
3. **Documentation as Infrastructure:** Docs are first-class, not afterthoughts
4. **Progressive Disclosure:** README gives quick start, docs/ has depth

## Integration Points

### Internal Integrations
- **Skeleton template:** Starting point for all new recipes
- **Documentation standards:** Templates for all documentation
- **Work logs:** Document development phases and methodology

### External Integrations
- **Docker Hub:** All recipes use official or well-maintained images
- **GitHub:** Repository hosting under radioastronomyio organization
- **Community:** Contributions via fork/PR workflow

## Architectural Decisions

### 2025-01-04: Three-File Recipe Pattern
**Decision:** Standardize on README.md, docker-compose.yml, .env.example as minimum recipe contents  
**Rationale:** Reduces complexity while maintaining usability; docs/ folder optional for complex recipes  
**Implications:** Faster recipe creation, consistent user experience

### 2025-01-04: Batch Processing Methodology
**Decision:** Process additions in batches of 6 with confirmation checkpoints  
**Rationale:** Prevents timeouts, enables verification between batches  
**Implications:** Systematic, reliable expansion process

### 2025-01-02: Database Category Restructure
**Decision:** Reorganize flat database-management/ into databases/ with subcategories by data model  
**Rationale:** Better taxonomy, accommodates vector databases, separates management tools  
**Implications:** Deeper nesting for database recipes, cleaner organization

### 2025-01-02: Interior README Pattern Adoption
**Decision:** Every directory gets a README following standard template  
**Rationale:** RAG optimization, human navigation, AI agent comprehension  
**Implications:** More files to maintain, but better discoverability

## Constraints and Limitations

- **Home Lab Focus:** Not designed for production without security hardening
- **Single-Node Default:** Multi-node setups documented but not default
- **Docker Compose Only:** No Kubernetes, Swarm, or other orchestrators
- **x86_64 Primary:** ARM support varies by upstream image availability

## Future Considerations

### Planned Improvements
- Consolidated stack recipes (full *Arr stack, observability stack)
- GitHub Actions for compose validation
- Automated testing for recipe syntax
- Cross-recipe integration examples

### Scalability Considerations
- Category structure scales well to 200+ recipes
- Interior README pattern maintains navigability at scale
- May need search/index tooling as recipe count grows further

### Known Technical Debt
- Some recipe docs/ folders are placeholder/incomplete
- Banner images not yet created for root README
- Some older recipes may need refresh to match current patterns
