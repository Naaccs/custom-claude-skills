# Coding Style

## Immutability by Default

- Prefer creating new values over mutating existing ones
- Mutation is acceptable in local scope, performance-critical paths, and when the language idiom demands it (e.g. Go structs, Python dicts in tight loops)

## Small Units

- Functions: aim for <50 lines, single responsibility
- Files: 200-400 lines typical, investigate at 800+
- Prefer many focused files over few large ones
- Organize by feature/domain, not by type

## Error Handling

- Handle errors explicitly — never swallow silently
- Let errors propagate to the appropriate boundary (middleware, error handler, caller)
- Don't log-and-rethrow in the same layer — pick one
- Error messages should help the developer debug, not expose internals to users

## Input Validation

- Validate at system boundaries: user input, external APIs, file I/O
- Trust internal function calls between your own modules
- Use the project's validation library (Zod, Pydantic, etc.) — don't hand-roll

## Secrets

- Never hardcode secrets, tokens, or credentials in source
- Use environment variables or secret managers
- If a secret is accidentally committed, treat it as compromised

## Before Marking Work Complete

- Code is readable and well-named
- Functions are focused and small
- No deep nesting (>4 levels — refactor)
- No leftover debug statements
- Errors are handled, not swallowed
- No magic numbers in business logic (extract named constants)
- All business logic is tested
