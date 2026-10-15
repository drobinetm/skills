# Skill: `token-discipline`

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](../LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skill-D97757)](https://docs.claude.com/en/docs/claude-code/skills)
[![Focus](https://img.shields.io/badge/focus-context%20%26%20tokens-blue)](#)

Rules to use context and tokens efficiently without sacrificing technical accuracy: locate before reading, do not re-read, batch independent work, filter output at the source, ignore structural noise, edit once, avoid repeating code, answer briefly and protect the context.

## Install

With the [`skills` CLI](https://github.com/vercel-labs/skills) (any supported agent):

```bash
npx skills add drobinetm/skills --skill token-discipline -a claude-code   # this project
npx skills add drobinetm/skills --skill token-discipline -g -a codex      # global, Codex
```

Or copy the folder to the directory your agent scans:

| Agent | Project | Global |
|-------|---------|--------|
| Claude Code | `.claude/skills/token-discipline/` | `~/.claude/skills/token-discipline/` |
| Codex | `.agents/skills/token-discipline/` | `~/.agents/skills/token-discipline/` |
| Gemini CLI | `.gemini/skills/` or `.agents/skills/` | `~/.gemini/skills/` or `~/.agents/skills/` |
| GitHub Copilot | `.github/skills/` or `.agents/skills/` | `~/.copilot/skills/` or `~/.agents/skills/` |
| Cursor | `.cursor/skills/` or `.agents/skills/` | `~/.cursor/skills/` or `~/.agents/skills/` |
| OpenCode | `.opencode/skills/` or `.agents/skills/` | `~/.config/opencode/skills/` or `~/.agents/skills/` |

Step-by-step instructions and links to each agent's guide are in the [root README](../README.md#install-per-agent).

## When it triggers

Working discipline for agent sessions that read code, run commands and edit files. The frontmatter `description` states the objective and asks to apply the skill in every session.

## What it enforces

| Area | Rule |
|------|------|
| Reading | Grep/Glob/`rg`/`git grep` first; then only the relevant region with `offset`/`limit`; justify in one sentence any read over 200 lines. |
| Re-reading | No re-reading to confirm an edit; an edit without error counts as applied. |
| Batching | Independent searches, reads and commands in one turn; no narrating turns. |
| Output | Filter at the source (`grep -n`, `rg -n`, `jq`, `git diff --stat`, `tail -50`); large JSON via `jq` or Python. |
| Noise | Skip `node_modules`, `.venv`, `venv`, `__pycache__`, `.git`, `dist`, `build`, `coverage`, `.next`, `.turbo`, `vendor`, `target`. |
| Editing | One complete pass; run tests once; at most two iterations on the same failure before changing approach. |
| Code in replies | Reference `path:line-range`; show only the diff or changed lines. |
| Final answer | Result first; no greetings or redundant summaries; no invented next step. |
| Context | No mid-task edits to `CLAUDE.md` or global config; suggest `/compact` when output goes stale. |
| Resolution order | Existing context, minimal fragment, local command or API/CLI, remote docs or browser last. |

## Requirements and agent compatibility

Plain `SKILL.md`; no tools required. Not yet tested on any agent.

## Contents

- `SKILL.md` — the instructions, as supplied by the author (translated to English, frontmatter added).
- `DECISIONS.md` — design decision log.

## When not to use it

When the user explicitly asks for an exhaustive read, a full-file review or verbose output.
