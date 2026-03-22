# CodeFlow Plugin for DevClaw

AI coding agent with a structured **Planning → Development → Review → Validation** workflow.

CodeFlow is a [DevClaw](https://github.com/jholhewres/devclaw) plugin that provides a methodical approach to implementing code changes. Instead of jumping straight into coding, it follows a structured workflow that plans first, develops incrementally, reviews automatically, and validates with tests.

## Features

- **4-stage workflow** — Planning, Development, Review, Validation (each individually toggleable)
- **Convention-aware** — auto-detects CLAUDE.md, .cursorrules, .editorconfig and follows project standards
- **Stack detection** — identifies languages, frameworks, and build tools automatically
- **Safety limits** — configurable max file changes per session to prevent runaway modifications
- **Change tracking** — logs every file mutation with timestamps for full auditability
- **Auto-validation** — runs tests, linter, and build checks with retry logic
- **Smart defaults** — works out of the box with zero configuration

## Installation

1. Clone or download this repository into your DevClaw plugins directory:

```bash
cd /path/to/your/plugins
git clone https://github.com/jholhewres/devclaw-plugin-codeflow.git codeflow
```

2. Add the plugins directory to your DevClaw config:

```yaml
plugins:
  dirs: ["./plugins"]
```

3. Restart DevClaw. The plugin will be discovered and loaded automatically.

## Usage

### Via Trigger Words

Send a message containing any of these trigger words to activate CodeFlow:

- `codeflow` — "codeflow: add pagination to the users API"
- `implement` — "implement a retry mechanism for HTTP calls"
- `code this` — "code this: dark mode toggle for settings page"
- `build this` — "build this feature: export data as CSV"
- `develop this` — "develop this: webhook handler for Stripe events"
- `write the code` — "write the code for user authentication"

### Via Delegation

From the main DevClaw agent, use:

```
delegate_to_plugin_agent(plugin_id="codeflow", agent_id="coder", task="Add rate limiting to the API gateway")
```

## Configuration

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| `stage_planning` | bool | `true` | Enable planning stage |
| `stage_development` | bool | `true` | Enable development stage |
| `stage_review` | bool | `true` | Enable code review stage |
| `stage_validation` | bool | `false` | Enable test/lint/build validation |
| `auto_approve_plan` | bool | `false` | Skip user approval of plans |
| `convention_file` | string | `""` | Path to conventions file (auto-detect if empty) |
| `test_command` | string | `""` | Custom test command (auto-detect if empty) |
| `lint_command` | string | `""` | Custom lint command (auto-detect if empty) |
| `build_command` | string | `""` | Custom build command (auto-detect if empty) |
| `max_file_changes` | int | `20` | Max files that can be modified per session |
| `working_directory` | string | `""` | Base directory for operations (empty = cwd) |

Configure via DevClaw's config.yaml:

```yaml
plugins:
  overrides:
    codeflow:
      stage_validation: true
      max_file_changes: 30
      test_command: "make test"
```

Or via the WebUI at `/plugins` → CodeFlow → Configure.

## Stages

### 1. Planning

Analyzes the request, detects the project stack, reads conventions, and produces a structured implementation plan for user approval.

### 2. Development

Executes the approved plan file by file, following conventions, tracking every change, and respecting safety limits.

### 3. Review

Generates a code review checklist from the git diff and reviews all changes for bugs, security issues, and convention adherence.

### 4. Validation

Runs the test suite (with up to 3 retries), linter, and build command to verify the implementation is correct.

## Tools

| Tool | Stage | Description |
|------|-------|-------------|
| `stage_status` | Setup | Returns current stage configuration |
| `plan_submit` | Planning | Submits structured implementation plan |
| `change_tracker` | Development | Tracks file mutations and enforces limits |
| `detect_stack` | Planning | Detects languages, frameworks, build tools |
| `conventions` | Planning | Reads project coding conventions |
| `review_checklist` | Review | Generates review checklist from diff |
| `run_tests` | Validation | Executes test suite |
| `run_lint` | Validation | Runs linter with optional auto-fix |
| `run_build` | Validation | Verifies compilation/build |
| `summary` | Final | Generates session summary |

## Skills

- **Planning** — Guide for creating effective implementation plans
- **Code Review** — Methodology for thorough code review
- **Conventions** — How to detect and follow project conventions
- **Testing** — Guide for writing and running tests

## License

MIT
