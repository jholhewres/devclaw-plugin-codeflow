# Testing and Validation

Guide for writing tests and validating code changes.

## Test Strategy

### When to Write Tests
- New public functions or methods
- Bug fixes (write a test that reproduces the bug first)
- Complex logic with multiple branches
- Integration points (API endpoints, database queries)

### When Tests Are Optional
- Simple getters/setters
- Configuration structs
- Generated code
- One-line wrapper functions

## Test Structure

### Unit Tests
- Test one thing per test case
- Use descriptive names: `TestUserService_CreateUser_DuplicateEmail`
- Arrange → Act → Assert pattern
- Table-driven tests for multiple inputs

### Integration Tests
- Test real dependencies when possible (databases, APIs)
- Use setup/teardown for test fixtures
- Tag or separate from unit tests for fast CI

## Validation Workflow

1. **Run tests** — execute the full test suite
2. **On failure**: read the error, identify the root cause, fix and retry (max 3 retries)
3. **Run linter** — check for code quality issues
4. **On lint errors**: auto-fix if possible, otherwise report
5. **Run build** — verify compilation succeeds
6. **On build failure**: analyze the error, fix, and retry once

## Auto-detection

The plugin auto-detects test frameworks:
- **Go**: `go test ./...`
- **Node.js**: Vitest, Jest, or `npm test`
- **Rust**: `cargo test`
- **Python**: pytest
- **Makefile**: `make test` (if target exists)
