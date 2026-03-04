# Health: Architecture Health Report

Run a full architecture health assessment on this repository.

## Instructions

### Step 1 — Repository Scan

Inspect the project using filesystem primitives:
- Glob for project structure and file types
- Grep for configuration patterns
- Read key config files (package.json, tsconfig, pyproject.toml, etc.)
- Check git status for uncommitted work

### Step 2 — Evaluate Each Dimension

Score each dimension as HEALTHY / WARNING / CRITICAL:

#### Stack Identification
- [ ] Languages detected and version-pinned
- [ ] Frameworks identified
- [ ] Build system present and configured
- [ ] Package manager lockfile committed

#### Type Safety
- [ ] Type system enabled (strict mode if TypeScript)
- [ ] No `any` types or untyped boundaries
- [ ] All public APIs are typed

#### Testing
- [ ] Test framework configured
- [ ] Tests exist and pass
- [ ] Test coverage is adequate (>70% for critical paths)
- [ ] Tests are hermetic and deterministic

#### Linting
- [ ] Linter configured
- [ ] Lint rules are strict enough
- [ ] No lint suppressions hiding real issues
- [ ] Custom rules for project-specific patterns

#### Build Reproducibility
- [ ] Lockfile present and committed
- [ ] No floating dependency versions
- [ ] Build produces consistent output
- [ ] CI/CD configuration present

#### Security
- [ ] No known vulnerabilities in dependencies
- [ ] No secrets in codebase
- [ ] Input validation at system boundaries
- [ ] Dependencies are maintained/active

#### Architecture Consistency
- [ ] Consistent folder structure
- [ ] No hybrid frameworks (e.g., mixed CJS/ESM)
- [ ] No partial migrations
- [ ] Clear separation of concerns

### Step 3 — Output the Report

```
## Architecture Health Report

### Overview
| Dimension | Status | Score |
|-----------|--------|-------|
| Stack | HEALTHY/WARNING/CRITICAL | details |
| Type Safety | HEALTHY/WARNING/CRITICAL | details |
| Testing | HEALTHY/WARNING/CRITICAL | details |
| Linting | HEALTHY/WARNING/CRITICAL | details |
| Build | HEALTHY/WARNING/CRITICAL | details |
| Security | HEALTHY/WARNING/CRITICAL | details |
| Architecture | HEALTHY/WARNING/CRITICAL | details |

### Overall Health: [HEALTHY / DEGRADED / CRITICAL]

### Critical Issues
[List any CRITICAL items that should block feature work]

### Recommended Actions
1. [Prioritized action items]
2. [...]

### Technical Debt Inventory
| Item | Severity | Effort | Impact |
|------|----------|--------|--------|
| ... | ... | ... | ... |
```

### Step 4 — Recommendations

If health is DEGRADED or CRITICAL:
- Recommend pausing feature work
- Propose a repair plan with specific steps
- Estimate the scope of repairs needed

If health is HEALTHY:
- Note any areas trending toward WARNING
- Suggest preventive measures
