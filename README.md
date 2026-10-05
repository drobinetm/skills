# skills

[![License: MIT](https://img.shields.io/github/license/drobinetm/skills)](LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/drobinetm/skills)](https://github.com/drobinetm/skills/commits/main)
[![Repo size](https://img.shields.io/github/repo-size/drobinetm/skills)](https://github.com/drobinetm/skills)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-skills-D97757)](https://docs.claude.com/en/docs/claude-code/skills)

A collection of Claude Code skills. Each skill lives in its own top-level folder with its entry point (`SKILL.md`) and its own `README.md` (what it does, how to install it, what it contains).

## Available skills

| Skill | Description |
|-------|-------------|
| [venuenexa-guide](venuenexa-guide/README.md) | Role-based session guide for the VenueNexa project (Ingenius): PV1-Tnn tasks, logbook and billable hours. |

## Installation

Copy (or symlink) the skill folder you want into your skills directory:

```bash
# Global (all projects)
cp -r <skill-name> ~/.claude/skills/

# Per project
cp -r <skill-name> <repo>/.claude/skills/
```

## Repository layout

```
<skill-name>/
  SKILL.md        # frontmatter (name, description) + workflow
  README.md       # the skill's own documentation
  references/     # material read on demand
```

## Adding a new skill

1. Create `<skill-name>/` at the repo root with `SKILL.md` and `README.md`.
2. Add a row to the table above.

## License

MIT — see [LICENSE](LICENSE).
