# Decision log - token-discipline

| ID | Date | Decision | Justification | Verified |
|---|---|---|---|---|
| D-01 | 2026-10-15 | Rules taken from the author's instructions with no added rules | User instruction: do not invent instructions | Yes: only change is `2&gt;&1` restored to `2>&1` (HTML escape in the pasted text) |
| D-02 | 2026-10-15 | Frontmatter added (`name: token-discipline`); name derived from the title | `SKILL.md` requires `name` and `description`; none were supplied | n/a |
| D-03 | 2026-10-15 | Content translated from Spanish to English | User request; also matches the Ingenius English-content standard | n/a |
| D-04 | 2026-10-15 | `description` extended with an "apply in every session ... even when the user does not mention tokens" clause | User asked for the skill to always be taken into account; skills trigger from the description, and the clause is the only always-on lever that does not touch global config | Not measured: trigger reliability unverified |
| D-05 | 2026-10-15 | Installed as a symlink `~/.claude/skills/token-discipline` -> project folder | Edits in the project stay in sync | Yes: see install check |
| D-06 | 2026-10-15 | README modelled on `venuenexa-guide/README.md`; "When not to use it" is the documenter's summary | Requested documentation format | n/a |

## Open verification
- Description-based activation is not a guarantee of always-on behavior; trigger reliability not measured.
