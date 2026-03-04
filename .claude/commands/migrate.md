# Migrate: Complete Migration Planning and Execution

Plan and execute a migration for: $ARGUMENTS

## Instructions

### CRITICAL RULE: No Partial Migrations

A partial migration is worse than no migration. Before starting, you MUST:
1. Scope the full migration
2. Identify every file that needs to change
3. Confirm the entire migration can be completed
4. Get explicit approval

If the migration is too large for one session, break it into self-contained phases where EACH phase leaves the system in a working state.

### Step 1 — Audit Current State

- Map all files affected by the migration
- Identify all dependencies on the code being migrated
- Check for runtime consumers (configs, scripts, CI, other services)
- Count the total scope: files, functions, tests

### Step 2 — Plan the Migration

```
## Migration Plan: [Description]

### Scope
- Files affected: [N]
- Functions/components affected: [N]
- Tests to update: [N]
- Config changes: [N]

### Migration Phases
Each phase must leave the system in a working, deployable state.

#### Phase 1: [Name]
- [ ] [Specific change]
- [ ] [Specific change]
- [ ] Verification: [What proves this phase is complete]

#### Phase 2: [Name]
- [ ] [Specific change]
...

### Breaking Changes
| Change | Impact | Migration Path |
|--------|--------|---------------|
| ... | ... | ... |

### Rollback Strategy
[How to undo each phase]

### Verification Criteria
- [ ] All tests pass
- [ ] No hybrid state (old + new coexisting)
- [ ] No dead code from old implementation
- [ ] All imports/references updated
- [ ] Build succeeds
- [ ] Lint passes
```

### Step 3 — Execute Phase by Phase

For each phase:
1. Implement the changes
2. Run all tests
3. Run lint and type check
4. Verify no hybrid state
5. Commit with clear message: `migrate: [phase description]`
6. Confirm the system works before moving to next phase

### Step 4 — Post-Migration Cleanup

- Remove all dead code from old implementation
- Remove old config files
- Update documentation if any
- Run `/health` to verify architecture is clean

### Rules

- NEVER leave the codebase in a hybrid state
- NEVER merge a partial migration to main
- If you discover the migration is bigger than expected, STOP and re-plan
- Every phase must pass all checks independently
- Keep the old code working until the new code is proven
