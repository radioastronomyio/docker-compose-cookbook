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
**Key Characteristics:** docker-compose.yml, .env.example, README.md, docs/ folder, optional scripts/

### Documentation Standards
**Purpose:** Templates ensuring consistent documentation across all recipes  
**Location:** `docs/documentation-standards/`  
**Key Characteristics:** Interior README template, recipe README template, tagging strategy, script headers

## Structure

```
docker-compose-cookbook/
├── databases/
│   ├── relational/           # SQL databases
│   ├── document/             # Document stores
│   ├── key-value/            # Key-value stores
│   ├── graph/                # Graph databases
│   ├── timeseries/           # Time series databases
│   ├── vector/               # Vector databases (AI/ML)
│   ├── wide-column/          # Wide-column stores
│   ├── management/           # Admin tools
│   └── README.md
├── networking/               # VPNs, DNS, ad blocking
├── monitoring-logging/       # Observability stack
├── automation-orchestration/ # Ansible, Rundeck, etc.
├── development-ci-cd/        # Git servers, CI/CD
├── storage-solutions/        # Object storage, sync
├── security/                 # Auth, secrets
├── container-management/     # Portainer, etc.
├── web-application-servers/  # Reverse proxies
├── messaging-collaboration/  # Chat, email
├── home-automation/          # Home Assistant, etc.
├── media-entertainment/      # Media servers
├── ai-ml/                    # LLM inference, ML tools
├── data-pipelines/           # Workflow orchestration
├── docs/
│   └── documentation-standards/
├── skeleton/                 # Template for new recipes
├── work-logs/                # Development phases
├── scratch/                  # Working files
└── README.md                 # Repository root
```

## Design Patterns and Principles

### Key Patterns

- **Interior README Pattern:** Every directory self-documents via README with tree structure and child links
- **Self-Contained Recipes:** Each recipe works independently without external dependencies
- **Environment Separation:** All configuration via .env files, never hardcoded
- **Documentation Hierarchy:** Recipe README → docs/ folder for extended content

### Design Principles

1. **Clone and Deploy:** Minimize steps from clone to running service
2. **Consistency Over Cleverness:** Same structure everywhere, even if slightly redundant
3. **Documentation as Infrastructure:** Docs are first-class, not afterthoughts
4. **Progressive Disclosure:** README gives quick start, docs/ has depth

## Integration Points

### Internal Integrations
- **Skeleton template:** Starting point for all new recipes
- **Documentation standards:** Templates for all documentation
- **Shared scripts:** Common utilities in `shared/` (future)

### External Integrations
- **Docker Hub:** All recipes use official or well-maintained images
- **GitHub:** Repository hosting, issues, PRs
- **Community:** Contributions via fork/PR workflow

## Architectural Decisions

### 2025-01-02: Database Category Restructure
**Decision:** Reorganize flat database-management/ into databases/ with subcategories by data model  
**Rationale:** Better taxonomy, accommodates vector databases, separates management tools  
**Alternatives Considered:** Keep flat structure, separate vector-databases category  
**Implications:** Deeper nesting for database recipes, cleaner organization

### 2025-01-02: Interior README Pattern Adoption
**Decision:** Every directory gets a README following standard template  
**Rationale:** RAG optimization, human navigation, AI agent comprehension  
**Alternatives Considered:** Central index file, wiki-style documentation  
**Implications:** More files to maintain, but better discoverability

### 2025-01-02: Remove Per-Recipe .github Folders
**Decision:** Consolidate issue templates to repository root  
**Rationale:** Reduces maintenance, .github only works at repo root anyway  
**Implications:** Less clutter in recipe directories

## Constraints and Limitations

- **Home Lab Focus:** Not designed for production without security hardening
- **Single-Node Default:** Multi-node setups documented but not default
- **Docker Compose Only:** No Kubernetes, Swarm, or other orchestrators
- **x86_64 Primary:** ARM support varies by upstream image availability

## Future Considerations

### Planned Improvements
- Add remaining planned recipes to each category
- Create GitHub Actions for compose validation
- Add automated testing for recipe syntax

### Scalability Considerations
- Category structure scales well to 100+ recipes
- May need search/index tooling as recipe count grows

### Known Technical Debt
- Some recipe docs are placeholder/incomplete
- Hardcoded URLs still reference old repository path in some files
- Some README casing inconsistent (readme.md vs README.md)
