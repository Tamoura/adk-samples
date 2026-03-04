# Plan: Structured Implementation Planning

Generate a structured implementation plan for: $ARGUMENTS

## Instructions

Follow this exact process:

### Step 1 — Context Discovery

Before planning, inspect the codebase:
- Use Glob to map the project structure
- Use Grep to find related code patterns
- Read key files that will be affected
- Identify the tech stack, test framework, and lint tools

### Step 2 — Produce the Plan

Output a structured plan in this exact format:

```
## Implementation Plan: [Feature Name]

### Summary
[1-2 sentence description of what will be built]

### Files to Modify
| File | Action | Description |
|------|--------|-------------|
| path/to/file | create/modify/delete | What changes |

### Implementation Steps
1. [Step with specific details]
2. [Step with specific details]
...

### Test Strategy
- [ ] [Specific test to write/run]
- [ ] [Specific test to write/run]

### Risk Assessment
| Risk | Severity | Mitigation |
|------|----------|------------|
| [Risk] | Low/Med/High | [How to handle] |

### Rollback Strategy
[How to undo these changes if something goes wrong]

### Dependencies
[Any new packages, APIs, or services required]

### Estimated Diff Surface
- Files: [N]
- Lines added: ~[N]
- Lines removed: ~[N]
```

### Step 3 — Wait for Approval

After presenting the plan, explicitly ask:
"Approve this plan to begin implementation?"

Do NOT write any implementation code until the plan is approved.

### Rules

- Plans must be specific — no vague steps like "implement the feature"
- Every file change must be listed
- Test strategy must include specific test names
- Risk assessment must be honest — if something is risky, say so
- If the feature touches infrastructure (build, CI, deps), flag it prominently
- If architectural issues are discovered during planning, report them and recommend fixing those first
