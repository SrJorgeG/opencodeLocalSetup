---
name: auto-commit-config
description: Use ALWAYS when modifying, creating, or deleting any configuration file in ~/.config/opencode/ or /home/jorge/.opencode/. Triggers on any change to opencode.json, skills, agents, MCPs, plugins, or .gitignore. Ensures changes are committed and pushed to their respective GitHub repositories with a detailed but brief commit message.
---

# Auto Commit and Push for OpenCode Config

Whenever any file in the following directories is modified, created, or deleted, you MUST commit and push the changes to the corresponding GitHub repository immediately after the edit is confirmed successful.

## Repositories

| Directory | Repository |
|-----------|------------|
| `~/.config/opencode/` | `git@github.com:SrJorgeG/opencodeGlobalConfig.git` |
| `/home/jorge/.opencode/` | `git@github.com:SrJorgeG/opencodeLocalSetup.git` |

## Trigger Conditions

Activate this skill when ANY of the following happen:
- Editing `opencode.json`, `opencode.jsonc`, or any JSON config file
- Creating, editing, or deleting a skill in `.opencode/skills/`
- Creating, editing, or deleting an agent in `.opencode/agent(s)/`
- Creating, editing, or deleting an MCP configuration
- Creating, editing, or deleting a plugin
- Modifying `.gitignore`
- Any other file change inside `~/.config/opencode/` or `/home/jorge/.opencode/`

## Commit Rules

1. **Stage only the relevant files** — do NOT commit `node_modules/`, backup files (`.bak`), log files, or temporary files.
2. **Write detailed but brief commit messages** in Spanish (since the user communicates in Spanish). Follow this format:
   - First line: summary under 50 characters
   - Blank line
   - Body: bullet points explaining what changed and why
3. **Push to the correct remote** based on which directory was modified.
4. **If both directories were modified**, commit and push each one separately.

## Example Commit Message

```
feat: añade skill auto-commit-config

- Crea skill para automatizar commits en config de OpenCode
- Cubre cambios en ~/.config/opencode/ y /home/jorge/.opencode/
- Incluye reglas de formato y repositorios destino
```

## Exceptions

- Do NOT commit if the only changes are inside `node_modules/`
- Do NOT commit if the user explicitly says "no hagas commit" or "skip commit"
- Do NOT commit temporary or backup files (`.bak`, `.tmp`, etc.)
