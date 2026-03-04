# Search: Deterministic Code Retrieval

Search the codebase for: $ARGUMENTS

## Instructions

Use the retrieval hierarchy — stop at the first level that gives you what you need. Do not over-search.

### Level 1 — Glob (File Discovery)

Start by finding relevant files:
- Search for files matching the query pattern
- Try common naming conventions: kebab-case, camelCase, snake_case, PascalCase
- Check likely directories (src/, lib/, app/, components/, utils/, etc.)

If you found the files you need, stop here and present results.

### Level 2 — Grep (Content Search)

If glob wasn't enough, search file contents:
- Search for the exact term
- Search for related terms (synonyms, abbreviations)
- Try regex patterns for structural matches (function definitions, class declarations, imports)

If you found what you need, stop here and present results.

### Level 3 — Read (Deep Inspection)

If grep found candidate files, read them to understand context:
- Read the full file, not just the matching line
- Follow imports and references to understand the dependency chain
- Check test files for usage examples

Present findings with file paths and line numbers.

### Level 4 — AST Analysis (Structural)

Only if the query is structural (e.g., "find all classes implementing X", "find all functions that call Y"):
- Analyze the code structure, not just text patterns
- Trace call chains
- Map dependency graphs

### Output Format

```
## Search Results: [query]

### Files Found
| File | Relevance | Key Lines |
|------|-----------|-----------|
| path/to/file.ts | [why it's relevant] | L42-L67 |

### Key Findings
[Summary of what was found and how it relates to the query]

### Related Code
[Any connected files, imports, or dependencies worth knowing about]

### Search Depth Used
[Which level(s) of the hierarchy were needed]
```

### Rules

- Always start at Level 1. Do not jump to grep without trying glob first.
- Present results concisely. File paths with line numbers, not walls of code.
- If nothing is found, say so clearly. Do not fabricate results.
- If the search reveals architectural issues, note them.
