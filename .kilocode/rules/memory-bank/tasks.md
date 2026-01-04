# Docker Compose Cookbook Tasks and Workflows

## Common Workflows

### Adding a New Recipe

**When to use:** Adding a new service to an existing category  
**Frequency:** Primary development activity

**Steps:**
1. Create recipe directory in appropriate category
2. Create `docker-compose.yml` with service configuration
3. Create `.env.example` with all configurable variables
4. Write `README.md` following recipe pattern (metadata, description, quick start, configuration, volumes, ports)
5. Test deployment locally: `docker compose up -d && docker compose logs`
6. Update parent category README.md to include new recipe in table
7. Commit and push

**Expected Outcome:** Deployable recipe with three-file structure  
**Common Issues:** Missing environment variables, incorrect volume paths, port conflicts

---

### Batch Recipe Addition (GDR Workflow)

**When to use:** Adding multiple recipes from research batch  
**Frequency:** Expansion phases

**Steps:**
1. **Research:** Use Google Deep Research to identify applications
2. **Planning:** Map applications to cookbook-canonical categories
3. **Directory Creation:** PowerShell one-liner for bulk structure:
   ```powershell
   @("app1","app2","app3") | ForEach-Object { New-Item -ItemType Directory -Path "category\$_" -Force }
   ```
4. **Batch Execution:** Process 6 recipes max per batch
5. **Confirmation:** Verify completion between batches
6. **Documentation:** Update category READMEs after all recipes complete

**Expected Outcome:** Multiple recipes with consistent quality  
**Critical:** Never exceed 6 items per batch to avoid timeouts

---

### Adding a New Category

**When to use:** New service type not covered by existing categories  
**Frequency:** Rare - structure is largely stable

**Steps:**
1. Create category directory at repository root
2. Create README.md following interior README template
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

### README Synchronization

**When to use:** After batch additions or structural changes  
**Frequency:** After expansion phases

**Steps:**
1. List all directories in category to get actual recipe inventory
2. Update category README with accurate recipe table
3. Update recipe counts
4. Change status from "Planned" to "Active" where applicable
5. Process in batches of 6 READMEs to avoid timeouts

**Expected Outcome:** All READMEs reflect actual repository contents  
**Critical:** Do this AFTER all recipes are in place, not during

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
7. Update repository statistics if counts changed

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
2. Update architecture.md if structure changed
3. Update product.md if goals/metrics changed
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
4. Update README if significant changes
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
- [ ] README.md has metadata, description, quick start, configuration
- [ ] Deploys successfully with `docker compose up -d`
- [ ] Container stays running (check with `docker compose ps`)
- [ ] Parent category README updated with recipe entry

### Documentation Quality Checklist
- [ ] YAML frontmatter present with correct tags
- [ ] Semantic section numbering preserved
- [ ] Links to related documents work
- [ ] Tree structure matches actual directory contents
- [ ] Recipe table status indicators accurate
- [ ] Recipe counts accurate

### Batch Processing Checklist
- [ ] Batch size ≤ 6 items
- [ ] Directory structure created upfront
- [ ] Confirmation checkpoint after each batch
- [ ] Documentation sync scheduled for after completion
- [ ] Worklog updated with methodology

### Commit Quality Checklist
- [ ] Descriptive commit message
- [ ] Related files grouped in single commit
- [ ] No sensitive data (passwords, keys) committed
- [ ] .env files excluded (only .env.example committed)
