# Skill: `precise-research`

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](../LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skill-D97757)](https://docs.claude.com/en/docs/claude-code/skills)
[![Focus](https://img.shields.io/badge/focus-factual%20accuracy-blue)](#)

Research and verification skill. Its objective is factual precision, not apparent helpfulness: every technical claim is checked against documentation or web search, labelled **[VERIFICADO]**, **[INFERIDO]** or **[DESCONOCIDO]**, and backed by a cited source. When evidence is insufficient the answer is “No tengo evidencia suficiente para afirmarlo.”

## Install

With the [`skills` CLI](https://github.com/vercel-labs/skills) (any supported agent):

```bash
npx skills add drobinetm/skills --skill precise-research -a claude-code   # this project
npx skills add drobinetm/skills --skill precise-research -g -a codex      # global, Codex
```

Or copy the folder to the directory your agent scans:

| Agent | Project | Global |
|-------|---------|--------|
| Claude Code | `.claude/skills/precise-research/` | `~/.claude/skills/precise-research/` |
| Codex | `.agents/skills/precise-research/` | `~/.agents/skills/precise-research/` |
| Gemini CLI | `.gemini/skills/` or `.agents/skills/` | `~/.gemini/skills/` or `~/.agents/skills/` |
| GitHub Copilot | `.github/skills/` or `.agents/skills/` | `~/.copilot/skills/` or `~/.agents/skills/` |
| Cursor | `.cursor/skills/` or `.agents/skills/` | `~/.cursor/skills/` or `~/.agents/skills/` |
| OpenCode | `.opencode/skills/` or `.agents/skills/` | `~/.config/opencode/skills/` or `~/.agents/skills/` |

Step-by-step instructions and links to each agent's guide are in the [root README](../README.md#install-per-agent).

## When it triggers

When the user asks to research, verify, fact-check, compare versions, find current documentation, or validate APIs, packages, commands or configurations, or asks any question where accuracy matters.

## What it enforces

| Area | Rule |
|------|------|
| Sources | Web search or documentation tools for versions, releases, changelogs, pricing, availability; APIs, SDKs, CLI flags, package names, endpoints; Python, Ansible, Docker, Kubernetes/OKD, Linux, Odoo; security advisories, compatibility matrices, configuration syntax. |
| Certainty | No unverified technical fact is stated as certain. |
| Labels | **[VERIFICADO]** supported by a cited source (exact source required) · **[INFERIDO]** reasonable deduction, explicitly uncertain · **[DESCONOCIDO]** no reliable evidence found. |
| Conflicts | If sources disagree, the conflict is reported instead of choosing silently. |
| No invention | URLs, citations, package/module names, CLI flags, Odoo models/fields/XML IDs/hooks/endpoints, Ansible parameters, Docker flags, Kubernetes fields, file paths, commands, outputs, benchmarks, version numbers. |
| Style | Result first; no greetings or restating the question; only necessary code, bullets or a short table; “Suposiciones” only when assumptions exist; “Verificación” with commands or sources when applicable. |
| Before proposing a command or config | Confirm tool/version, confirm the parameter exists in official docs, prefer official docs over blogs or AI-generated content, request minimum evidence (error output, `--version`, relevant file) if the environment matters. |
| Safety | No destructive operation without an explicit dry-run or backup step. |

## Requirements and agent compatibility

The skill is plain `SKILL.md`. It relies on the agent having web search or documentation tools (for example Context7 or WebSearch/WebFetch in Claude Code). Without them it cannot mark anything **[VERIFICADO]** and should answer with **[INFERIDO]**/**[DESCONOCIDO]** or the “No tengo evidencia suficiente” reply. Not yet tested on any agent.

## Contents

- `SKILL.md` — the instructions, as supplied by the author.
- `DECISIONS.md` — design decision log.

## When not to use it

Tasks that do not depend on factual accuracy of external technical facts, such as creative writing or refactoring code whose behavior is already given in the conversation.
