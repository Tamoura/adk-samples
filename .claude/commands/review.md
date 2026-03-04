# Review: Deterministic Self-Review

Run a thorough self-review on the current changes in this repository.

## Instructions

### Step 1 — Gather the Diff

Run `git diff` and `git diff --staged` to see all current changes. Also run `git status` to check for untracked files.

### Step 2 — Review Checklist

Evaluate every change against this checklist:

#### Correctness
- [ ] Does the code do what it's supposed to do?
- [ ] Are edge cases handled?
- [ ] Are error conditions handled at system boundaries?
- [ ] Do all new code paths have test coverage?

#### Security (OWASP Top 10)
- [ ] No command injection (user input in shell commands)
- [ ] No XSS (user input in HTML output)
- [ ] No SQL injection (user input in queries)
- [ ] No hardcoded secrets or credentials
- [ ] No insecure deserialization
- [ ] No path traversal vulnerabilities

#### Type Safety
- [ ] No `any` types introduced (TypeScript)
- [ ] No type assertions that could be unsafe (`as` casts)
- [ ] All function parameters and returns are typed
- [ ] Null/undefined handled explicitly

#### Code Quality
- [ ] No dead code introduced
- [ ] No unused imports
- [ ] No premature abstractions
- [ ] No unnecessary complexity
- [ ] Consistent naming conventions
- [ ] Self-documenting — comments only where logic isn't obvious

#### Scope Discipline
- [ ] Changes are scoped to the intended feature/fix
- [ ] No unrelated modifications
- [ ] No formatting-only changes to untouched code
- [ ] Diff surface is minimal

#### Testing
- [ ] New tests are hermetic (no network, no shared state)
- [ ] New tests are deterministic (same result every time)
- [ ] Test names are descriptive
- [ ] Existing tests still pass

### Step 3 — Pattern Detection

Look for recurring issues. If you find any pattern that has appeared before:
1. Note it explicitly
2. Suggest a lint rule or automated check to prevent it
3. Recommend adding it to `/lint/custom-rules/` or the project's lint config

### Step 4 — Output the Review

Format your review as:

```
## Code Review Report

### Summary
[1-2 sentence summary of changes reviewed]

### Issues Found
| # | Severity | File:Line | Issue | Recommendation |
|---|----------|-----------|-------|----------------|
| 1 | Critical/High/Medium/Low | path:line | Description | Fix |

### Checklist Results
- Correctness: PASS/FAIL
- Security: PASS/FAIL
- Type Safety: PASS/FAIL
- Code Quality: PASS/FAIL
- Scope Discipline: PASS/FAIL
- Testing: PASS/FAIL

### Recurring Patterns Detected
[Any patterns that should become automated rules]

### Verdict
APPROVE / REQUEST CHANGES / BLOCK
[Justification]
```

If there are issues, fix them before presenting the review unless they require user decision.
