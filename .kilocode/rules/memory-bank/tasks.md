# Docker Compose Cookbook Tasks and Workflows

## Common Workflows

### Adding a New Recipe

**When to use:** Adding a new service to an existing category  
**Frequency:** Primary development activity

**Steps:**
1. Copy skeleton template to appropriate category directory
   ```bash
   cp -r skeleton/ category/subcategory/new-recipe/
   ```
2. Create `docker-compose.yml` with service configuration
3. Create `.env.example` with all configurable variables
4. Write `README.md` following `docs/documentation-standards/recipe-readme-template.md`
5. Create docs/ folder with CONFIGURATION.md, SECURITY.md, TROUBLESHOOTING.md at minimum
6. Test deployment locally: `docker compose up -d && docker compose logs`
7. Update parent category README.md to include new recipe in table
8. Commit and push

**Expected Outcome:** Deployable recipe with full documentation  
**Common Issues:** Missing environment variables, incorrect volume paths, port conflicts

---

### Adding a New Category

**When to use:** New service type not covered by existing categories  
**Frequency:** Rare - structure is largely stable

**Steps:**
1. Create category directory at repository root
2. Create README.md following `docs/documentation-standards/interior-readme-template.md`
3. Add category to root README.md category table
4. Update architecture.md in memory bank
5. Commit changes

**Expected Outcome:** Empty category ready for recipes  
**Common Issues:** Forgetting to update root README

---

### Updating Existing Recipe

**When to use:** Fixing issues, updating versions, improving documentation  
**Frequency:** Ongoing maintenance

**Steps:**
1. Navigate to recipe directory
2. Make necessary changes to compose file, docs, or configuration
3. Test locally if compose changes made
4. Update recipe README.md if significant changes
5. Commit with descriptive message

**Expected Outcome:** Updated, working recipe  
**Common Issues:** Breaking changes in upstream images

---

## Memory Bank Maintenance

### Updating context.md

**When:** After every significant work session  
**What to update:**
1. Move completed items from "Next Steps" to "Recent Accomplishments"
2. Update "Current Phase" if phase changed
3. Update "Next Steps" with new actionable items
4. Document any new decisions in "Recent Decisions"
5. Add/resolve blockers as appropriate
6. Update "Last Updated" date

**Quality check:** Does context.md accurately reflect current state?

---

### Session Start Procedure

**Objective:** Load context and confirm understanding

1. Read brief.md and context.md
2. Check "Last Updated" date - if stale, review what's changed
3. Review "Next Steps" for session priorities
4. Confirm understanding with operator

---

### Session End Procedure

**Objective:** Update memory bank with session outcomes

1. Update context.md with accomplishments and next steps
2. Update other memory bank files if architecture/tech changed
3. Update scratch/session-checkpoint.md if using
4. Commit memory bank changes

---

## Maintenance Tasks

### Validate All Compose Files

**When to use:** Before releases or after bulk changes  
**Frequency:** Periodic

```bash
# Find and validate all compose files
find . -name "docker-compose.yml" -exec docker compose -f {} config --quiet \;
```

**Expected Outcome:** All files pass validation  
**Common Issues:** YAML syntax errors, invalid service definitions

---

### Update Docker Image Tags

**When to use:** Updating to new upstream versions  
**Frequency:** Quarterly or as needed

**Steps:**
1. Check Docker Hub for new image versions
2. Update image tag in docker-compose.yml
3. Test deployment with new version
4. Update UPGRADING.md with version notes
5. Commit changes

---

### Bulk README Updates

**When to use:** Repository-wide changes (URLs, format, etc.)  
**Frequency:** Rare

```powershell
# Example: Update repository URLs
Get-ChildItem -Recurse -Filter "README.md" | ForEach-Object { 
    (Get-Content $_.FullName) -replace 'old-pattern', 'new-pattern' | Set-Content $_.FullName 
}
```

---

## Quality Checklists

### Recipe Quality Checklist
- [ ] docker-compose.yml uses v2 syntax (no version key)
- [ ] .env.example includes all variables with descriptions
- [ ] README.md follows recipe template
- [ ] docs/ folder has CONFIGURATION.md at minimum
- [ ] Deploys successfully with `docker compose up -d`
- [ ] Container stays running (check with `docker compose ps`)
- [ ] Parent category README updated with recipe entry

### Documentation Quality Checklist
- [ ] YAML frontmatter present with correct tags
- [ ] Semantic section numbering preserved
- [ ] Links to related documents work
- [ ] Tree structure matches actual directory contents
- [ ] Recipe table status indicators accurate

### Commit Quality Checklist
- [ ] Descriptive commit message
- [ ] Related files grouped in single commit
- [ ] No sensitive data (passwords, keys) committed
- [ ] .env files excluded (only .env.example committed)
