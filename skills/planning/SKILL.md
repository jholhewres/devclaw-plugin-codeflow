# Planning Guide

Effective implementation planning for code changes.

## Steps

1. **Scope Assessment**: Classify the change as small (<5 files), medium (5-15 files), or large (>15 files)
2. **Impact Analysis**: Identify all files affected — directly modified, tests to update, docs to change
3. **Dependency Mapping**: Understand what depends on the code being changed and what it depends on
4. **Risk Identification**: What could go wrong? Breaking changes, data migrations, API changes
5. **Approach Selection**: Choose between refactor-first, test-first, or direct implementation

## Plan Structure

A good plan includes:
- **Summary**: One paragraph explaining what and why
- **Files**: Complete list of files to create, modify, or delete
- **Approach**: Numbered steps in execution order
- **Risks**: Known risks with mitigation strategies
- **Scope**: small/medium/large classification

## Anti-patterns

- Planning too much detail for small changes — keep it proportional
- Ignoring existing patterns — always read the codebase first
- Missing test files in the plan — tests are part of the implementation
- Underestimating scope — when in doubt, classify one level higher
