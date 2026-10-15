---
name: token-discipline
description: Optimize context and token usage without sacrificing technical accuracy. Apply in every session and on every task that reads files, searches code, runs commands, edits files or writes replies, even when the user does not mention tokens or context.
---

# TOKEN DISCIPLINE

Optimize context and token usage without sacrificing technical accuracy.

## Mandatory rules

1. **Locate before reading.**
   - Use Grep, Glob, `rg`, `git grep` or indexes before opening files.
   - Then read only the relevant region with `offset` and `limit`.
   - Do not read a whole file if 30–100 lines answer the question.
   - If you need to read more than 200 lines, justify why in one sentence.

2. **Do not re-read without need.**
   - Do not re-read a file just to "verify" that an edit worked.
   - If the edit tool returned no error, consider the edit applied.
   - Re-read only if the file changed externally, if an error requires it, or if you need a different section.

3. **Batch independent work.**
   - Run independent searches, reads and commands in the same turn.
   - Do not make one call per file when you can inspect several targets at once.
   - Avoid intermediate turns that only narrate what you are about to do.

4. **Filter output at the source.**
   - Do not paste full outputs into the context.
   - Use filters before showing results:
     - `grep -n "pattern" file`
     - `rg -n "pattern" --glob '!node_modules'`
     - `jq '.field' file.json`
     - `git diff --stat`
     - `git log --oneline -20`
     - `command 2>&1 | tail -50`
   - For large JSON, use `jq` or Python; do not open it in full.

5. **Ignore structural noise.**
   - Do not explore by default: `node_modules`, `.venv`, `venv`, `__pycache__`, `.git`, `dist`, `build`, `coverage`, `.next`, `.turbo`, `vendor`, `target`.
   - Use `--glob` or suitable exclusions in searches.

6. **Write once, precisely.**
   - Before editing, understand the code and the relevant tests.
   - Make the complete change in one pass when possible.
   - Run tests once; if they fail, read the error, fix once, and repeat only if necessary.
   - Do not iterate more than twice on the same failure without rethinking the approach.

7. **Do not repeat code unnecessarily.**
   - Do not paste long unchanged blocks.
   - Reference code as `path/file.py:123-145`.
   - Show only the diff or the modified lines.

8. **Keep the final answer short.**
   - Result first.
   - No greetings, no redundant summaries, no courtesy phrases.
   - At most: result, diff/command, verification and next step.
   - If no next step is needed, do not invent one.

9. **Protect the context.**
   - Do not edit `CLAUDE.md`, global configuration or session context mid-task unless truly necessary.
   - When the conversation accumulates obsolete outputs, suggest `/compact`.
   - Keep in the summary: current task, edited files, decisions made and pending errors.

## Resolution order

1. Answer from the context already available.
2. Search or read the minimum fragment needed.
3. Run a local command or query an API/CLI if needed.
4. Use a browser or remote documentation only if there is no sufficient local alternative.

## Forbidden

- Reading whole files by default.
- Re-reading freshly edited files to confirm the edit.
- Running commands with massive unfiltered output.
- Exploring generated directories or dependencies.
- Repeating explanations, code or context already present.
- Making tool calls in series when they are independent.
