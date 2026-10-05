# skills

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/drobinetm/skills)](https://github.com/drobinetm/skills/commits/main)
[![Repo size](https://img.shields.io/github/repo-size/drobinetm/skills)](https://github.com/drobinetm/skills)
[![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills%20(SKILL.md)-blue)](#how-skills-are-structured)
[![Agents](https://img.shields.io/badge/agents-Claude%20Code%20%7C%20Codex%20%7C%20Gemini%20CLI%20%7C%20Copilot%20%7C%20Cursor%20%7C%20OpenCode-informational)](#install-per-agent)

A collection of agent skills. Each skill is a top-level folder with its entry point (`SKILL.md`) and its own `README.md`. Skills use the open `SKILL.md` format (folder + YAML frontmatter with `name` and `description`), so they are not tied to a single agent.

## Available skills

| Skill | Description |
|-------|-------------|
| [venuenexa-guide](venuenexa-guide/README.md) | Role-based session guide for the VenueNexa project (Ingenius): PV1-Tnn tasks, logbook and billable hours. |

## Quick install (any agent)

The [`skills` CLI](https://github.com/vercel-labs/skills) installs a skill into one or more agents and puts it in the right directory for each:

```bash
# See what this repo offers
npx skills add drobinetm/skills --list

# Install one skill, into the current project, for specific agents
npx skills add drobinetm/skills --skill venuenexa-guide -a claude-code -a codex

# Install globally (all projects) instead of per project
npx skills add drobinetm/skills --skill venuenexa-guide -g

# Manage
npx skills list
npx skills update
npx skills remove venuenexa-guide
```

Useful flags: `-g` global, `-a <agent>` target agent, `-s <skill>` pick a skill, `--copy` copy files instead of symlinking, `-y` skip prompts. Run `npx skills --help` for the current list of supported agents and flags.

## Install per agent

If you prefer not to use the CLI, copy the skill folder to the path your agent scans. Replace `<skill>` with the folder name (e.g. `venuenexa-guide`).

| Agent | Project path | Global (user) path | Guide |
|-------|--------------|--------------------|-------|
| Claude Code | `.claude/skills/<skill>/` | `~/.claude/skills/<skill>/` | [Skills docs](https://code.claude.com/docs/en/skills) |
| Codex (CLI / IDE) | `.agents/skills/<skill>/` | `~/.agents/skills/<skill>/` | [Codex skills](https://developers.openai.com/codex/skills) |
| Gemini CLI | `.gemini/skills/<skill>/` or `.agents/skills/<skill>/` | `~/.gemini/skills/<skill>/` or `~/.agents/skills/<skill>/` | [Gemini CLI skills](https://geminicli.com/docs/cli/skills/) |
| GitHub Copilot | `.github/skills/<skill>/`, `.claude/skills/<skill>/` or `.agents/skills/<skill>/` | `~/.copilot/skills/<skill>/` or `~/.agents/skills/<skill>/` | [About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) |
| Cursor | `.cursor/skills/<skill>/` or `.agents/skills/<skill>/` | `~/.cursor/skills/<skill>/` or `~/.agents/skills/<skill>/` | [Cursor skills](https://cursor.com/docs/context/skills) |
| OpenCode | `.opencode/skills/<skill>/`, `.claude/skills/<skill>/` or `.agents/skills/<skill>/` | `~/.config/opencode/skills/<skill>/`, `~/.claude/skills/<skill>/` or `~/.agents/skills/<skill>/` | [OpenCode skills](https://opencode.ai/docs/skills/) |

> Paths were taken from each agent's documentation (checked 2026-10-05). Agents change these locations between releases; if a skill does not show up, check the linked guide first. `.agents/skills/` is the most widely shared location (Codex, Gemini CLI, Copilot, Cursor and OpenCode all read it), so it is the safest project-level choice for a multi-agent team.

### Claude Code

```bash
# Global
git clone https://github.com/drobinetm/skills.git
cp -r skills/venuenexa-guide ~/.claude/skills/

# Or per project (commit it so the whole team gets it)
cp -r skills/venuenexa-guide .claude/skills/
```

Edits to an existing `SKILL.md` are picked up automatically. For a newly added skill folder, run `/reload-skills` (or restart the session), then invoke it with `/venuenexa-guide` or let it trigger from its description.

### Codex

```bash
cp -r skills/venuenexa-guide ~/.agents/skills/      # user scope
cp -r skills/venuenexa-guide .agents/skills/        # repo scope
```

Invoke from the Codex CLI/IDE with `/skills` or by typing `$venuenexa-guide`. Codex also reads `/etc/codex/skills` for admin-wide skills.

### Gemini CLI

```bash
gemini skills install https://github.com/drobinetm/skills.git --consent
gemini skills list --all
```

Use `--scope workspace` or `--scope user` to choose where it goes, and `--path <subdir>` to install a single skill from this repo. Manual copy to `~/.gemini/skills/` or `.gemini/skills/` also works.

### GitHub Copilot

```bash
cp -r skills/venuenexa-guide .github/skills/        # project
cp -r skills/venuenexa-guide ~/.copilot/skills/     # personal
```

Per the docs, agent skills work with the Copilot cloud agent, code review, Copilot CLI, and agent mode in VS Code and JetBrains.

### Cursor

```bash
cp -r skills/venuenexa-guide .cursor/skills/        # project
cp -r skills/venuenexa-guide ~/.cursor/skills/      # user
```

Cursor discovers skills at startup, and also loads them from Claude and Codex directories. `name` must be lowercase letters, numbers and hyphens only.

### OpenCode

```bash
cp -r skills/venuenexa-guide .opencode/skills/              # project
cp -r skills/venuenexa-guide ~/.config/opencode/skills/     # global
```

OpenCode also reads `.claude/skills/` and `.agents/skills/`, so a skill installed for Claude Code is already visible to it. The skill `name` must match its folder name.

### Other agents

Most agents that support the `SKILL.md` format scan a skills directory like the ones above. Use `npx skills add drobinetm/skills --list` and `npx skills add ... -a <agent>` to see whether your agent is supported, or check its documentation for the skills path.

## How skills are structured

```
<skill-name>/
  SKILL.md        # frontmatter (name, description) + workflow
  README.md       # the skill's own documentation
  references/     # material read on demand
```

Keep the folder name equal to the `name` in the frontmatter, lowercase with single hyphens. That satisfies the strictest agents (Cursor, OpenCode) and works everywhere else.

## Adding a new skill

1. Create `<skill-name>/` at the repo root with `SKILL.md` and `README.md`.
2. Add a row to the table above.
3. Check it is detected: `npx skills add . --list`.

## License

MIT — see [LICENSE](LICENSE).
