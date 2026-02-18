# Repository Context

This is a documentation repository — a centralized, version-controlled collection of coding standards, architecture patterns, and process documentation. These docs are designed to be imported into other projects to provide consistent AI context.

## Project Purpose

This repository serves as a single source of truth for:
- **Coding standards** (naming, TypeScript conventions, Prisma patterns, etc.)
- **Architecture decisions** (React component patterns, server actions, etc.)
- **Process documentation** (how to write docs, how to work)
- **AI context files** (IDE-specific orchestrators and rules)

A separate CLI tool (not in this repo) allows developers to fetch specific docs into their projects.

## Repository Structure

```
docs/               # Pure documentation content
  standards/        # How to write code
  architecture/     # How to structure code
  process/          # How to work

ai/                 # IDE-specific AI context files
  copilot/   # Copilot orchestrators and instructions
  cursor/           # Cursor orchestrators and rules
```

### Key Principles

**Content Layer (`docs/`):**
- Each document is standalone and technology-focused
- No dependencies between docs
- Clean markdown, no IDE-specific details
- Named by technology (typescript.md, prisma.md), not by project

**AI Context Layer (`ai/`):**
- IDE-specific (one subfolder per IDE)
- Reference docs/ content rather than duplicating
- Orchestrators guide AI to read relevant docs
- Granular files auto-apply to matching file patterns

## Common Tasks

When working in this repository, you'll typically be asked to:

### Writing Documentation
- Create new standard/architecture/process docs in `docs/`
- Keep content reusable and project-agnostic
- Use clear examples and avoid jargon
- Follow the structure in `docs/process/documentation.md`

### Maintaining AI Context
- Update orchestrator files when docs/ structure changes
- Create granular instruction files for specific technologies
- Ensure AI context references docs rather than duplicating content
- Keep file patterns aligned with IDE capabilities

### Consistency & Quality
- Ensure naming conventions are consistent across docs
- Verify cross-references between docs are accurate
- Check that AI orchestrators reflect the current docs/ tree
- Keep tone professional, concise, and actionable

## Writing Guidelines

- **Tone:** Direct and actionable. No fluff.
- **Structure:** Use headings, lists, and code examples liberally
- **Scope:** Each doc covers ONE technology or concept
- **Portability:** Docs should work in any project using that technology
- **Examples:** Show real code, not pseudocode

## When Contributing

1. Read existing docs in the relevant category to match style
2. Keep `docs/` technology-focused and standalone
3. Update AI orchestrators if you add/remove/restructure docs
4. Test that cross-references and links are valid
5. Avoid duplicating content — link to other docs instead
