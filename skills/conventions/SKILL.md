# Convention Detection and Adherence

How to detect and follow project coding conventions.

## Detection Sources (Priority Order)

1. **CLAUDE.md** — AI-specific project instructions (highest priority)
2. **.cursorrules** — Cursor IDE rules (same format as CLAUDE.md)
3. **CONVENTIONS.md** — Explicit convention documentation
4. **.editorconfig** — Editor formatting rules
5. **Existing code** — Infer from patterns in the codebase

## What to Look For

### Naming
- Variables: camelCase vs snake_case vs PascalCase
- Files: kebab-case vs snake_case vs camelCase
- Functions: verb-first (getUser) vs noun-first (userGet)
- Constants: UPPER_SNAKE vs PascalCase

### Structure
- File organization: by feature vs by type
- Import ordering: stdlib first, third-party, local
- Export patterns: named vs default exports

### Error Handling
- Return errors vs throw/panic
- Error wrapping patterns
- Logging conventions

### Testing
- Test file location: colocated vs separate directory
- Naming: Test_FunctionName vs describe/it
- Mocking approach: interfaces vs libraries

## Adherence Rules

1. **Match, don't improve** — follow existing conventions even if you'd do it differently
2. **Be consistent** — if the file uses tabs, use tabs; if it uses 2-space indent, use 2 spaces
3. **Follow the majority** — when conventions vary within a project, follow the most common pattern
4. **New files follow conventions** — when creating new files, match the style of similar existing files
