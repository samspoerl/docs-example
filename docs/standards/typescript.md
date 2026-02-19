TypeScript Standards

Goals
- Strong types for public APIs.
- Minimal type gymnastics.

General
- Use `unknown` over `any` at boundaries.
- Prefer `type` for simple shapes, `interface` for public contracts.
- Avoid type assertions; narrow instead.

Types
- Use literal unions for finite sets.
- Model optional fields explicitly with `?`.
- Prefer `Readonly` for immutable inputs.

Functions
- Type parameters when they add clarity, not ceremony.
- Keep return types explicit for exported functions.

Errors
- Use typed error classes for domain errors.
- Never throw strings.

Imports
- Use path aliases for shared modules.
- Prefer named exports for consistency.

Linting
- Resolve all TypeScript errors before merge.
