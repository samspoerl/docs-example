# docs-example

Example docs registry used with the [**docs-cli**](https://github.com/samspoerl/docs-cli). This repo shows how to structure a docs registry and AI context so the CLI can pull it into projects.

## How It Works

The repo has two layers:

| Layer | Folder | What It Is | How It's Consumed |
|-------|--------|-----------|-------------------|
| **Content** | `docs/` | Pure knowledge — standards, architecture, process. Clean markdown. No IDE awareness. | CLI copies files as-is into target project |
| **AI Context** | `ai/` | IDE-specific files that *reference* docs and control *when/how* AI applies them. One subfolder per IDE. | CLI routes files to the correct IDE location |

### Content Layer (`docs/`)

Organized by concern, named by technology. Each file is a standalone document — no dependencies between docs.

```
docs/
  standards/         ← How to write code
  architecture/      ← How to structure code
  process/           ← How to work
```

A "stack" (e.g., Next.js + Prisma + TypeScript) is just a *selection* of docs, not a folder. The same `typescript.md` applies whether you're building with Next.js or Remix.

### AI Context Layer (`ai/`)

Each IDE subfolder contains:

1. **An orchestrator** — Always sent to the AI. Contains the full docs tree with short descriptions. Lightweight. The AI reads this and decides which docs it needs for the current task.
2. **Granular files** — Matched by glob pattern (e.g., all `.ts` files). Ensures specific context is auto-attached for matching files.

```
ai/
  copilot/
    copilot-instructions.md              ← Orchestrator (always sent)
    instructions/
      typescript.instructions.md         ← Auto-applied to *.ts, *.tsx
  cursor/
    orchestrator.mdc                     ← Orchestrator (always applied)
    rules/
      typescript.mdc                     ← Auto-applied to *.ts, *.tsx
```

The AI context files **reference** docs rather than duplicating them. Example: a Copilot instruction file says *"Follow the standards in `docs/standards/typescript.md`"* — the AI reads the referenced file when it needs deeper context.

## Companion CLI

The [docs-cli](https://github.com/samspoerl/docs-cli) fetches docs from this registry and writes them into a target project, similar to shadcn's CLI model:

- `docs add typescript prisma` — Cherry-pick specific docs
- `docs add standards` — Pull an entire category
- Auto-detects IDE and routes AI context files to the correct location

The CLI always fetches the latest from `main`. No versioning complexity.

> Note: If the docs repo is private, you need a GitHub PAT with content read access.

## Project Status

Early discovery and experimentation. The final structure may change.

### Parked / Exploratory

Exploring if/how to integrate parts of the agentic IDE stack (e.g., agents, skills, MCP, etc.). Skills and MCP configs may be better installed directly from their source tools rather than maintained here.