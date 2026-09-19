---
name: agent-index
description: >
  Use the per-repo .agent-index/ (files.tsv, symbols.tsv, topics.md, vectors)
  before grepping the tree or reading source files. Regenerates with
  `agent-index index`. Search with `agent-index search "query"`. Use when
  exploring a codebase, finding a function by name, locating
  authentication/CGI/RBAC files, or when the user mentions agent-index, code
  index, embeddings, or reading only a function range.
---

# Agent index

If `.agent-index/meta.json` is missing or `agent-index status` prints `stale`/`missing`, run `agent-index index` in the repo root. Do not wander the tree first.

Then, in order:

1. Natural language / concept → `agent-index search "<query>"` (vectors via FreeLLMAPI `bge-m3`; falls back to symbols.tsv).
2. Known symbol name → `rg '^<name>\t' .agent-index/symbols.tsv`.
3. Topic list → `rg -i <concept> .agent-index/topics.md`.
4. Read that path only from `start` to `end` (not the whole file).
5. Full-file read is a last resort: index missing after a failed regenerate, or the range is clearly wrong.

Do not search `node_modules`, build dirs, or the whole repo for a symbol that is in `symbols.tsv`.
If `status` has no `family=`, grep only; embeddings need FreeLLMAPI on `:3001`.

CLI: `agent-index index` / `status` / `search` (requires `~/.local/bin` on PATH).
