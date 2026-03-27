# Performance

## Context Window Management
- Avoid large-scale refactoring or multi-file features in the last 20% of context
- Reserve low-context for: single-file edits, simple bug fixes, documentation
- If context is getting heavy, finish the current unit of work and suggest continuing in a new session

## Code Performance Defaults
- Don't optimize prematurely — write clear code first, profile if slow
- Avoid unnecessary allocations in hot paths (loops, frequent callbacks)
- Prefer lazy evaluation and early returns over deep processing
- Cache expensive computations when the inputs are stable
- Be aware of N+1 query patterns in any data access layer

## Build & CI Failures
- Read the full error message before acting
- Fix incrementally — one issue at a time
- Verify after each fix before moving on
- Don't bypass linters or type checkers to "make it green"
