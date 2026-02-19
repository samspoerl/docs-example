Coding Principles

Purpose
- Keep code readable first, clever second.
- Optimize for change, not perfection.

Core Principles
- Single responsibility per module or function.
- Prefer explicit over implicit behavior.
- Fail fast with clear errors.
- Keep dependencies minimal and obvious.
- Make side effects easy to spot.

Naming
- Use intent-revealing names.
- Avoid abbreviations unless common to the domain.
- Prefer verbs for functions, nouns for data.

Structure
- Keep functions small and linear.
- Avoid deep nesting; extract helpers.
- Group related code by feature, not type.

Error Handling
- Validate inputs at boundaries.
- Wrap external calls with contextual errors.
- Do not swallow errors; log or rethrow.

Testing
- Test behavior, not implementation details.
- Prefer fewer, higher-signal tests.
- Cover critical paths and edge cases.

Code Review Checklist
- Readability at first glance.
- Clear ownership of side effects.
- Consistent patterns with nearby code.
- No hidden performance traps.
