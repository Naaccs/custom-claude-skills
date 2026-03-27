# Custom Claude Code Rules & Agents

A collection of custom rules and agents for [Claude Code](https://claude.com/claude-code).

## Rules

Global rules that shape how Claude approaches work across all projects.

| Rule | Description |
|------|-------------|
| [coding-style.md](rules/coding-style.md) | Immutability by default, small functions, explicit error handling, input validation |
| [testing.md](rules/testing.md) | Test behavior not implementation, independent tests, match project patterns |
| [performance.md](rules/performance.md) | Context window management, lazy evaluation, N+1 prevention, caching strategies |

## Agents

Specialized subagents that handle focused tasks autonomously.

| Agent | Model | Description |
|-------|-------|-------------|
| [architect.md](agents/architect.md) | opus | System design, scalability analysis, architectural decisions |
| [codebase-analyzer.md](agents/codebase-analyzer.md) | sonnet | Precise code analysis with file references and data flow tracing |
| [codebase-locator.md](agents/codebase-locator.md) | haiku | Fast file/component location across codebases |
| [codebase-pattern-finder.md](agents/codebase-pattern-finder.md) | sonnet | Find existing code patterns to use as templates |
| [devils-advocate.md](agents/devils-advocate.md) | sonnet | Critical review that challenges assumptions and finds real problems |
| [e2e-runner.md](agents/e2e-runner.md) | sonnet | E2E testing with Vercel Agent Browser / Playwright |
| [tdd-guide.md](agents/tdd-guide.md) | sonnet | Test-driven development enforcement with 80%+ coverage |
| [web-search-researcher.md](agents/web-search-researcher.md) | sonnet | Web research for API docs, libraries, and best practices |

## Installation

### Rules

Copy any rule file into `~/.claude/rules/`:

```bash
# Single rule
curl -o ~/.claude/rules/coding-style.md https://raw.githubusercontent.com/nicholasvarley/custom-claude-skills/main/rules/coding-style.md

# All rules
for f in coding-style testing performance; do
  curl -o ~/.claude/rules/$f.md https://raw.githubusercontent.com/nicholasvarley/custom-claude-skills/main/rules/$f.md
done
```

### Agents

Copy any agent file into `~/.claude/agents/`:

```bash
# Single agent
curl -o ~/.claude/agents/architect.md https://raw.githubusercontent.com/nicholasvarley/custom-claude-skills/main/agents/architect.md

# All agents
for f in architect codebase-analyzer codebase-locator codebase-pattern-finder devils-advocate e2e-runner tdd-guide web-search-researcher; do
  curl -o ~/.claude/agents/$f.md https://raw.githubusercontent.com/nicholasvarley/custom-claude-skills/main/agents/$f.md
done
```
