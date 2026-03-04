# AI Engineering Operating System for Claude Code

A structured operating system that configures Claude Code to work with plan-first execution, safety guardrails, and deterministic review loops.

## Quick Start

Open this repo in Claude Code. The `CLAUDE.md` file is automatically loaded, enforcing the engineering operating model on every session.

## Available Commands

| Command | Purpose |
|---------|---------|
| `/plan <feature>` | Generate a structured implementation plan before writing code |
| `/review` | Run a deterministic self-review on current changes |
| `/health` | Produce an architecture health report for the project |
| `/guardrails` | Check and enforce all safety guardrails |
| `/search <query>` | Search the codebase using the retrieval hierarchy |
| `/metrics` | Generate an AI engineering metrics report |
| `/scaffold <type>` | Bootstrap project infrastructure (TS, Python, etc.) |
| `/migrate <target>` | Plan and execute a complete migration |

## How It Works

### CLAUDE.md
The master instruction file. Claude Code reads this on every session and follows the operating principles: plan-first, infrastructure-first, deterministic review, safety guardrails.

### .claude/commands/
Custom slash commands that encode specific workflows. Each command is a structured prompt that guides Claude Code through a repeatable process.

### .claude/settings.json
Permission and hook configuration. Includes a pre-tool hook that blocks destructive commands like `rm -rf /`, `git push --force`, and `--no-verify` bypasses.

### ai/templates/
JSON schemas for structured outputs:
- **plan-template.json** — Schema for machine-verifiable implementation plans
- **review-checklist.json** — Deterministic review checklist with check IDs
- **review-patterns.json** — Tracker for recurring review feedback (auto-generates lint rules at threshold)
- **health-report.json** — Architecture health report structure

### lint/custom-rules/
Directory for auto-generated lint rules. As review patterns recur, they get converted into automated checks placed here.

## Operating Principles

1. Plan before code
2. Infrastructure before features
3. Determinism over cleverness
4. Complete migrations only
5. Guardrails over manual review
6. Simplicity beats sophistication
7. No partial system states

## Portability

To use this system in another repo, copy these files:
```
CLAUDE.md
.claude/commands/
.claude/settings.json
ai/templates/
lint/custom-rules/.gitkeep
```
