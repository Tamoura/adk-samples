# Guardrails: Safety Check and Enforcement

Run all safety guardrails on the current state of the repository.

## Instructions

### Step 1 — Detect Available Tooling

Check what safety tools are configured:
- Look for `package.json` scripts (test, lint, typecheck, build)
- Look for `tsconfig.json` (TypeScript)
- Look for `.eslintrc*` or `eslint.config.*` (ESLint)
- Look for `pyproject.toml` with ruff/pytest config (Python)
- Look for `Makefile`, `justfile`, or CI configs
- Look for pre-commit hooks in `.husky/` or `.git/hooks/`

### Step 2 — Run Available Checks

Execute every check that is configured. Run in parallel where possible:

1. **Type check** — `npx tsc --noEmit` or equivalent
2. **Lint** — `npx eslint .` or `ruff check .` or equivalent
3. **Tests** — `npm test` or `pytest` or equivalent
4. **Security audit** — `npm audit` or `pip audit` if available
5. **Build** — `npm run build` if configured

### Step 3 — Static Analysis

Even without tooling, manually check for:

#### File Safety
- [ ] No files deleted without explicit approval in this session
- [ ] No writes outside project directory
- [ ] No modifications to CI/CD without approval
- [ ] No dependency changes without approval

#### Secret Detection
- [ ] No hardcoded API keys, tokens, or passwords
- [ ] No `.env` files staged for commit
- [ ] No private keys or certificates in repo
- [ ] No connection strings with credentials

#### Code Safety
- [ ] No `eval()` or dynamic code execution
- [ ] No unsanitized user input in commands/queries
- [ ] No disabled security features (CORS *, auth bypass)
- [ ] No `--no-verify` or `--force` in scripts

### Step 4 — Output Report

```
## Guardrails Report

### Automated Checks
| Check | Status | Details |
|-------|--------|---------|
| Type check | PASS/FAIL/SKIP | [output summary] |
| Lint | PASS/FAIL/SKIP | [output summary] |
| Tests | PASS/FAIL/SKIP | [output summary] |
| Security audit | PASS/FAIL/SKIP | [output summary] |
| Build | PASS/FAIL/SKIP | [output summary] |

### Manual Checks
| Check | Status | Details |
|-------|--------|---------|
| File safety | PASS/FAIL | [details] |
| Secret detection | PASS/FAIL | [details] |
| Code safety | PASS/FAIL | [details] |

### Overall: ALL CLEAR / ISSUES FOUND / BLOCKED

### Issues to Resolve
[List any failures with specific fix instructions]
```

### Step 5 — Enforce

If any check FAILS:
- Do NOT proceed with committing or pushing
- Fix the issues first
- Re-run the failing checks
- Only proceed when all checks pass

If a check is SKIPPED (tooling not available):
- Note it as a gap
- Recommend adding the tooling
- Do not block on it
