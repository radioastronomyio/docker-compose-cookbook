# AGENTS.md

Entry point for AI coding agents working on this repository.

## Project Identity

**Domain:** Docker / Self-Hosting / Infrastructure
**Repository:** https://github.com/radioastronomyio/docker-compose-cookbook
**Purpose:** Curated Docker Compose configurations for self-hosted services. Each recipe provides copy-and-deploy configurations with sensible defaults, environment templates, and comprehensive documentation covering configuration, security, performance tuning, and troubleshooting. 100+ recipes across 14 categories.

## Current State

**Phase:** Active, ongoing recipe additions
**Date:** March 2026

### What Exists

- **100+ recipes** across 14 categories (AI/ML, databases, monitoring, networking, media, security, etc.)
- **Standardized recipe structure:** `docker-compose.yml` + `.env.example` + `README.md` + optional `docs/` and `scripts/`
- **Category READMEs** with subcategory organization and recipe indexes
- **Documentation standards** in `docs/documentation-standards/`

### Categories

| Category | Directory | Recipes |
|----------|-----------|---------|
| AI & Machine Learning | `ai-ml/` | 21 |
| Automation & Orchestration | `automation-orchestration/` | 8 |
| Container Management | `container-management/` | 3 |
| Databases | `databases/` | 20 |
| Development & CI/CD | `development-ci-cd/` | 9 |
| Home Automation | `home-automation/` | 1 |
| Media & Entertainment | `media-entertainment/` | 8 |
| Messaging & Collaboration | `messaging-collaboration/` | 2 |
| Monitoring & Logging | `monitoring-logging/` | 13 |
| Networking | `networking/` | 10 |
| Personal Utilities | `personal-utilities/` | 8 |
| Security | `security/` | 2 |
| Storage Solutions | `storage-solutions/` | 6 |
| Web Application Servers | `web-application-servers/` | 6 |

## Key Constraints

- Every recipe must follow the standardized structure (docker-compose.yml, .env.example, README.md)
- `.env.example` is committed; `.env` is gitignored
- Recipes should work out of the box with `docker compose up -d` after `.env` customization
- Documentation covers configuration, security considerations, and troubleshooting
- GPU-accelerated recipes require NVIDIA Container Toolkit

## Execution Environment

**Primary execution:** ML01 (`/opt/repos/docker-compose-cookbook/`)
**Agent runtime:** OpenCode (global config at `~/.config/opencode/opencode.json`)
**Session management:** aoe (Agent of Empires)
**Strategic work:** Claude.ai Projects
**Agentic coding:** Claude Code, OpenCode

## Recipe Structure

Every recipe follows this pattern:

```
recipe-name/
├── docker-compose.yml    # Main compose configuration
├── .env.example          # Environment template (copy to .env)
├── README.md             # Quick start and overview
├── docs/                 # Extended documentation (optional)
│   ├── CONFIGURATION.md
│   ├── SECURITY.md
│   └── TROUBLESHOOTING.md
└── scripts/              # Helper scripts (optional)
```

## Repository Structure

```
docker-compose-cookbook/
├── ai-ml/                          # AI & Machine Learning recipes
├── automation-orchestration/       # Automation & workflow engines
├── container-management/           # Container orchestration tools
├── data-pipelines/                 # Data pipeline tools
├── databases/                      # SQL, NoSQL, vector, graph, time series
├── development-ci-cd/              # Git servers, CI/CD, dev tools
├── home-automation/                # Smart home platforms
├── media-entertainment/            # Media servers, *Arr stack
├── messaging-collaboration/        # Push notifications, newsletters
├── monitoring-logging/             # Metrics, visualization, logs
├── networking/                     # VPNs, DNS, reverse proxies
├── personal-utilities/             # Knowledge management, productivity
├── security/                       # Auth, secrets, password vaults
├── storage-solutions/              # File sync, backup, document mgmt
├── web-application-servers/        # CMS, no-code, business apps
├── assets/                         # Images, banners
├── docs/
│   └── documentation-standards/    # Templates, tagging strategy
├── internal-files/                 # Working documents
├── shared/                         # Cross-project utilities
├── spec/                           # Specifications
├── staging/                        # Staged work (gitignored)
├── work-logs/                      # Development history
├── AGENTS.md                       # This file
├── CLAUDE.md                       # Pointer to AGENTS.md
├── LICENSE                         # MIT
└── README.md
```

## Conventions

- **Documentation:** Use templates from `docs/documentation-standards/`
- **Commits:** Conventional commits (`feat:`, `fix:`, `docs:`)
- **Frontmatter:** YAML frontmatter with tags from `docs/documentation-standards/tagging-strategy.md`
- **Interior READMEs:** Every directory has one
- **Recipe naming:** lowercase, hyphenated (e.g., `gitea-postgresql`, `nginx-proxy-manager`)

## Related Repositories

| Repository | Relationship |
|-----------|-------------|
| `proxmox-astronomy-lab` | Infrastructure where recipes may be deployed |
| `project-template-repository` | Base scaffolding patterns |
