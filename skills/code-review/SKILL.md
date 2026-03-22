# Code Review Methodology

Systematic approach to reviewing code changes.

## Review Categories

### Critical (Must Fix)
- Logic errors and bugs
- Security vulnerabilities (injection, auth bypass, data exposure)
- Data loss or corruption risks
- Race conditions and deadlocks

### Warning (Should Fix)
- Missing error handling
- Performance issues (N+1 queries, unnecessary allocations)
- Inadequate input validation
- Missing tests for critical paths

### Info (Consider)
- Code style inconsistencies
- Naming improvements
- Documentation gaps
- Refactoring opportunities

## Review Process

1. Read the diff as a whole to understand the overall change
2. Check each file against the project's conventions
3. Verify error handling paths
4. Look for edge cases (nil, empty, boundary values)
5. Check for security implications
6. Verify test coverage for new code
7. Summarize findings by severity

## Common Issues by Language

### Go
- Unchecked errors, missing defer for cleanup, goroutine leaks, mutex misuse

### TypeScript/JavaScript
- Missing null checks, unhandled promise rejections, XSS via innerHTML, missing dependencies in useEffect

### Python
- Bare except clauses, mutable default arguments, missing type hints on public APIs
