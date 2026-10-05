# Skill: `venuenexa-guide`

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](../LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skill-D97757)](https://docs.claude.com/en/docs/claude-code/skills)
[![Project](https://img.shields.io/badge/project-VenueNexa-blue)](#)
[![Roles](https://img.shields.io/badge/roles-PM%20%7C%20Analyst%20%7C%20Architect%20%7C%20Dev%20%7C%20DevOps%20%7C%20QA-informational)](references/roles)

Interactive guide for working on the VenueNexa project (Ingenius, Zoho INGENIUS-238, tasks PV1-Tnn). It interviews the team member (in Spanish) and walks them through the agent-first session ritual: review open tasks, pick one, assume the task's role (PM, Analyst, Architect, Dev, DevOps, QA), work with role-specific questions, and close with a change summary, WorkDrive upload, role logbook entry and billable hours.

## Install

```bash
cp -r venuenexa-guide ~/.claude/skills/
```

Requires Zoho (Projects + WorkDrive) and GitLab connections; without them it runs in guidance-only mode.

## Contents

- `SKILL.md` — initial triage, step table and non-negotiable rules.
- `references/session-start.md`, `role-onboarding.md`, `working-rules.md`, `human-decisions.md`, `session-close.md`, `project-context.md` — read when entering each step.
- `references/roles/` — per-role questions and context (pm, analyst, architect, dev, devops, qa).
- `evals/evals.json` — cases for measuring trigger reliability.
- `DECISIONS.md` — design decision log for this skill.

## When not to use it

Generic Zoho/GitLab questions unrelated to VenueNexa, or Ingenius-wide architecture rules (use `architectural-principles`, `arc42-template`, `adr`, `operating-model`).
