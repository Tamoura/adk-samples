# Scaffold: Bootstrap Project Infrastructure

Set up a new project or add infrastructure to an existing one: $ARGUMENTS

## Instructions

### Step 1 — Assess Current State

Inspect what exists:
- Check for package.json / pyproject.toml / go.mod
- Check for tsconfig / .eslintrc / ruff config
- Check for test framework configuration
- Check for CI/CD configuration
- Check for existing code structure

### Step 2 — Determine What's Needed

Based on the project type and what's missing, plan the scaffold:

#### TypeScript/Node.js Project
- [ ] `package.json` with scripts: build, test, lint, typecheck
- [ ] `tsconfig.json` with strict: true
- [ ] `.eslintrc.json` with strict rules
- [ ] `vitest.config.ts` or `jest.config.ts`
- [ ] `.gitignore` (node_modules, dist, .env)
- [ ] Source directory structure (`src/`, `tests/`)
- [ ] `npm install` for all dependencies

#### Python Project
- [ ] `pyproject.toml` with ruff + pytest config
- [ ] Type checking config (mypy/pyright)
- [ ] `.gitignore` (__pycache__, .venv, .env)
- [ ] Source directory structure
- [ ] Virtual environment setup

### Step 3 — Present the Plan

Show exactly what will be created/modified. Wait for approval.

### Step 4 — Implement

Create all files. Run:
- Install dependencies
- Verify build works
- Verify tests run (even if no tests yet)
- Verify lint passes
- Verify type check passes

### Step 5 — Verify

Run `/guardrails` to confirm everything is clean.

### Rules

- Always use strict typing configurations
- Always include a test framework
- Always include a linter
- Always create a .gitignore
- Never use loose/permissive configs — start strict, relax only when justified
- Prefer modern tooling (vitest over jest, ruff over flake8, ESM over CJS)
