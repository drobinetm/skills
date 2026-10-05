# Skill: `venuenexa-guide`

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](../LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skill-D97757)](https://docs.claude.com/en/docs/claude-code/skills)
[![Project](https://img.shields.io/badge/project-VenueNexa-blue)](#)
[![Roles](https://img.shields.io/badge/roles-PM%20%7C%20Analyst%20%7C%20Architect%20%7C%20Dev%20%7C%20DevOps%20%7C%20QA-informational)](references/roles)

Interactive guide for working on the VenueNexa project (Ingenius, Zoho INGENIUS-238, tasks PV1-Tnn). It interviews the team member (in Spanish) and walks them through the agent-first session ritual: review open tasks, pick one, assume the task's role (PM, Analyst, Architect, Dev, DevOps, QA), work with role-specific questions, and close with a change summary, WorkDrive upload, role logbook entry and billable hours.

## Install

With the [`skills` CLI](https://github.com/vercel-labs/skills) (any supported agent):

```bash
npx skills add drobinetm/skills --skill venuenexa-guide -a claude-code   # this project
npx skills add drobinetm/skills --skill venuenexa-guide -g -a codex      # global, Codex
```

Or copy the folder to the directory your agent scans:

| Agent | Project | Global |
|-------|---------|--------|
| Claude Code | `.claude/skills/venuenexa-guide/` | `~/.claude/skills/venuenexa-guide/` |
| Codex | `.agents/skills/venuenexa-guide/` | `~/.agents/skills/venuenexa-guide/` |
| Gemini CLI | `.gemini/skills/` or `.agents/skills/` | `~/.gemini/skills/` or `~/.agents/skills/` |
| GitHub Copilot | `.github/skills/` or `.agents/skills/` | `~/.copilot/skills/` or `~/.agents/skills/` |
| Cursor | `.cursor/skills/` or `.agents/skills/` | `~/.cursor/skills/` or `~/.agents/skills/` |
| OpenCode | `.opencode/skills/` or `.agents/skills/` | `~/.config/opencode/skills/` or `~/.agents/skills/` |

Step-by-step instructions and links to each agent's guide are in the [root README](../README.md#install-per-agent).

## Requirements and agent compatibility

The skill itself is plain `SKILL.md` + Markdown references, so any agent that supports the format can load it. What it does at runtime depends on the tools the agent has:

- **Zoho (Projects + WorkDrive) and GitLab access:** needed to list tasks, upload documents and log hours. Without them the skill runs in guidance-only mode and never pretends a write happened.
- **Interactive questions:** the skill asks with `AskUserQuestion` when the agent provides it (Claude Code) and falls back to plain-text questions otherwise.
- **Tested on:** Claude Code. Other agents are expected to load it but have not been tested.

## Contents

- `SKILL.md` — initial triage, step table and non-negotiable rules.
- `references/session-start.md`, `role-onboarding.md`, `working-rules.md`, `human-decisions.md`, `session-close.md`, `project-context.md` — read when entering each step.
- `references/roles/` — per-role questions and context (pm, analyst, architect, dev, devops, qa).
- `evals/evals.json` — cases for measuring trigger reliability.
- `DECISIONS.md` — design decision log for this skill.

## When not to use it

Generic Zoho/GitLab questions unrelated to VenueNexa, or Ingenius-wide architecture rules (use `architectural-principles`, `arc42-template`, `adr`, `operating-model`).
