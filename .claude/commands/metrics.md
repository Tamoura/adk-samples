# Metrics: AI Engineering Metrics Report

Generate an engineering metrics report for the current session or project state.

## Instructions

### Step 1 — Gather Data

Collect metrics from available sources:
- `git log` — commit history, frequency, diff sizes
- `git diff` — current change surface
- Test results — pass/fail rates
- Lint results — violation counts
- File structure — project organization health

### Step 2 — Compute Metrics

Calculate the following where data is available:

#### Execution Metrics
- **Plan-to-implementation accuracy**: Did the plan match what was built?
- **One-shot success rate**: How often did implementations work on first try?
- **Diff surface**: Files and lines changed per feature
- **Commit frequency**: How often are changes committed?

#### Quality Metrics
- **Test coverage trend**: Is coverage increasing or decreasing?
- **Lint violation trend**: Are violations increasing or decreasing?
- **Type safety coverage**: What percentage of code is strictly typed?
- **Guardrail coverage**: What percentage of review patterns are automated?

#### Health Metrics
- **Dependency freshness**: How many deps are outdated?
- **Build reliability**: Does the build pass consistently?
- **Architecture consistency**: Any hybrid states or partial migrations?

### Step 3 — Output Report

```
## Engineering Metrics Report
Date: [current date]
Scope: [session / project]

### Execution
| Metric | Value | Trend |
|--------|-------|-------|
| Plan accuracy | [%] | [up/down/stable] |
| One-shot success | [%] | [up/down/stable] |
| Avg diff surface | [N files, N lines] | [up/down/stable] |
| Commit frequency | [N/day or N/session] | [up/down/stable] |

### Quality
| Metric | Value | Trend |
|--------|-------|-------|
| Test coverage | [%] | [up/down/stable] |
| Lint violations | [N] | [up/down/stable] |
| Type safety | [%] | [up/down/stable] |
| Guardrail coverage | [%] | [up/down/stable] |

### Health
| Metric | Value | Status |
|--------|-------|--------|
| Dependency freshness | [N outdated] | [OK/WARN/CRIT] |
| Build reliability | [pass/fail] | [OK/WARN/CRIT] |
| Architecture consistency | [clean/hybrid] | [OK/WARN/CRIT] |

### Recommendations
1. [Actionable improvement based on metrics]
2. [...]
```

### Notes

- For first-run or empty repos, report baseline values and mark everything as "initial"
- Compare against previous reports if available
- Focus on trends, not absolute numbers
- Metrics that can't be measured should be listed as "N/A — [reason]"
- Suggest what tooling would enable unmeasurable metrics
