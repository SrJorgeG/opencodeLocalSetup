---
name: agent-index
description: >
  Use the per-repo .agent-index/ (files.tsv, symbols.tsv, topics.md) before
  grepping the tree or reading source files. Regenerates with `agent-index index`.
  Use when exploring a codebase, finding a function by name, locating
  authentication/CGI/RBAC files, or when the user mentions agent-index, code
  index, or reading only a function range.
---

# Agent index

If `.agent-index/meta.json` is missing or `agent-index status` prints `stale`/`missing`, run `agent-index index` in the repo root. Do not wander the tree first.

Then, in order:

1. `rg -i <concept> .agent-index/topics.md` — which files matter.
2. `rg '^<name>\t' .agent-index/symbols.tsv` — `path start end`.
3. Read that path only from `start` to `end` (not the whole file).
4. Full-file read is a last resort: index missing after a failed regenerate, or the range is clearly wrong.

Do not search `node_modules`, build dirs, or the whole repo for a symbol that is in `symbols.tsv`.
Embeddings are later (v1.5) — ignore if absent.

CLI: `agent-index index` / `agent-index status` (requires `~/.local/bin` on PATH).
