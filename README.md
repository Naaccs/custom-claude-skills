# Custom Claude Code Rules, Agents & Commands

A collection of custom rules, agents, and commands for [Claude Code](https://claude.com/claude-code).

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

## Commands

Custom slash commands for project workflows.

| Command | Model | Description |
|---------|-------|-------------|
| [tdd-plan.md](commands/tdd-plan.md) | opus | Create implementation plans with explicit TDD phases, research-driven context gathering, and agent orchestration |
| [test-walkthrough.md](commands/test-walkthrough.md) | opus | Browser-based walkthrough to verify features or debug issues using agent-browser in headed mode |

## Installation

### Rules

Copy any rule file into `~/.claude/rules/`:

```bash
# Single rule
curl -o ~/.claude/rules/coding-style.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/rules/coding-style.md

# All rules
for f in coding-style testing performance; do
  curl -o ~/.claude/rules/$f.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/rules/$f.md
done
```

### Agents

Copy any agent file into `~/.claude/agents/`:

```bash
# Single agent
curl -o ~/.claude/agents/architect.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/agents/architect.md

# All agents
for f in architect codebase-analyzer codebase-locator codebase-pattern-finder devils-advocate e2e-runner tdd-guide web-search-researcher; do
  curl -o ~/.claude/agents/$f.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/agents/$f.md
done
```

### Commands

Copy any command file into your project's `.claude/commands/` directory:

```bash
mkdir -p .claude/commands

# Single command
curl -o .claude/commands/tdd-plan.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/commands/tdd-plan.md

# All commands
for f in tdd-plan test-walkthrough; do
  curl -o .claude/commands/$f.md https://raw.githubusercontent.com/Naaccs/custom-claude-skills/main/commands/$f.md
done
```
