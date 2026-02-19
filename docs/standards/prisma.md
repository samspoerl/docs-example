Prisma Standards

Schema
- Keep models small and focused.
- Prefer explicit relation names for clarity.
- Use `@@index` for common filter paths.

Migrations
- One migration per logical change.
- Name migrations by intent, not timestamp.
- Review generated SQL before applying in prod.

Queries
- Use `select` to limit data returned.
- Favor `findUnique` with stable keys.
- Keep transactions short and narrow.

Error Handling
- Map Prisma errors to domain errors.
- Do not leak Prisma error codes to callers.

Performance
- Avoid n+1 by using `include` or batching.
- Use pagination with `take` and `cursor`.
