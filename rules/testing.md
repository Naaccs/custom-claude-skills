# Testing

## Defaults
- Write tests for non-trivial logic — utils, business rules, API endpoints
- Test coverage expectations are set per-project, not globally
- Match the project's existing test patterns and framework

## Principles
- Test behavior, not implementation details
- Each test should be independent — no shared mutable state between tests
- When a test fails, fix the implementation first; only fix the test if the test itself is wrong
- Prefer fast, focused unit tests; add integration/E2E where the project requires it

## When Adding Features
- If the project has tests, add tests for your new code
- If the project has no tests, don't introduce a test framework without asking
- Run existing tests before and after your changes to catch regressions
