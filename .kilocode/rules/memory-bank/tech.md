# Docker Compose Cookbook Technology Stack

## Technology Stack

### Primary Technologies
- **Docker:** 20.10+ - Container runtime
- **Docker Compose:** 2.0+ - Multi-container orchestration
- **YAML:** - Configuration format for compose files
- **Markdown:** - Documentation format

### Supporting Technologies
- **Git:** - Version control
- **PowerShell:** - Maintenance scripts (Windows)
- **Bash:** - Maintenance scripts (Linux/Mac)

## Dependencies

### Required Dependencies
```
Docker Engine >= 20.10
Docker Compose >= 2.0 (v2 syntax, not legacy docker-compose)
```

### Optional Dependencies
```
Git                    # For cloning and contributing
Text editor            # For customizing .env files
```

## Development Environment

### Prerequisites
- Docker Desktop (Windows/Mac) or Docker Engine (Linux)
- Git for cloning the repository
- Text editor for configuration

### Setup Instructions

```bash
# Clone repository
git clone https://github.com/radioastronomyio/docker-compose-cookbook.git
cd docker-compose-cookbook

# Navigate to desired recipe
cd databases/relational/mysql

# Copy environment template
cp .env.example .env

# Edit configuration
nano .env  # or your preferred editor

# Deploy
docker compose up -d

# Verify
docker compose ps
docker compose logs
```

### Environment Variables

Each recipe uses its own `.env` file. Common patterns:

```bash
CONTAINER_NAME=service-name     # Container identifier
PORT=NNNN                       # Host port mapping
TZ=America/New_York             # Timezone
PUID=1000                       # User ID for permissions
PGID=1000                       # Group ID for permissions
```

## Infrastructure

### Runtime Environment
- **Platform:** Any Docker-capable host (Linux, Windows, Mac)
- **Resources:** Varies by recipe (see individual README)
- **Network:** Docker bridge networks by default

### Storage
- Docker named volumes for persistence
- Bind mounts optional for configuration files

## Technical Constraints

### Compatibility Requirements
- Docker Compose v2 syntax (no `version:` key needed)
- Official or well-maintained Docker images
- x86_64 architecture primary (ARM varies by image)

### Security Constraints
- Designed for home lab use
- Production deployment requires security hardening
- Secrets in .env files (not committed to git)

## Development Workflow

### Version Control
- **Repository:** https://github.com/radioastronomyio/docker-compose-cookbook
- **Branching Strategy:** main + feature branches
- **Commit Conventions:** Conventional commits preferred

### Adding New Recipes

```bash
# Copy skeleton template
cp -r skeleton/ category/new-recipe/

# Customize files
# - docker-compose.yml
# - .env.example
# - README.md
# - docs/*.md

# Test locally
docker compose up -d
docker compose logs

# Submit PR
git checkout -b add/new-recipe
git add .
git commit -m "feat(category): add new-recipe"
git push origin add/new-recipe
```

## Automation and Tooling

### Available Scripts
- `shared/generate_tree.py` - Generate directory tree for READMEs
- `scratch/restructure-categories.ps1` - Category migration (one-time)

### Maintenance Commands

```powershell
# Remove version lines from compose files
Get-ChildItem -Recurse -Filter "*compose.yml" | ForEach-Object { 
    (Get-Content $_.FullName) -notmatch '^\s*version:\s*[''"]' | Set-Content $_.FullName 
}

# Normalize README casing
Get-ChildItem -Recurse -Filter "readme.md" | Rename-Item -NewName "README.md"

# Update repository URLs
Get-ChildItem -Recurse -Filter "README.md" | ForEach-Object { 
    (Get-Content $_.FullName) -replace 'vintagedon/', 'radioastronomyio/' | Set-Content $_.FullName 
}
```

## Troubleshooting

### Common Issues

#### Container won't start
**Problem:** Service fails to start after `docker compose up`  
**Solution:** Check logs with `docker compose logs`, verify .env configuration, ensure ports aren't in use

#### Permission denied on volumes
**Problem:** Container can't write to mounted volumes  
**Solution:** Set PUID/PGID in .env to match host user, or adjust directory permissions

#### Port already in use
**Problem:** Error binding to port  
**Solution:** Change PORT in .env, or stop conflicting service

### Debug Commands

```bash
# Check container status
docker compose ps

# View logs
docker compose logs -f

# Shell into container
docker compose exec <service> /bin/sh

# Reset and rebuild
docker compose down -v
docker compose up -d --build
```

## Technical Documentation

- **Docker Compose:** https://docs.docker.com/compose/
- **Docker Hub:** https://hub.docker.com/
- **Internal Standards:** `docs/documentation-standards/`
