# Closing a task

Order matters: nothing is uploaded before the user has seen what changes, and hours are logged only after the user confirms them.

1. **Change summary (before upload).** List files created/changed, what changed in each, and what stays untouched. Ask: ¿Apruebas subir esto?
2. **Upload.** On approval, upload to WorkDrive (TeamFolder VenueNexa, correct subfolder), then verify by listing/reading the file back. Report the result truthfully; if verification fails, say so.
3. **Logbook entry.** Which method applies depends on where the role's logbook lives (ONBOARDING and ADR-VN-0005, both read live; if they differ from this file, WorkDrive wins):
   - **WorkDrive roles (PM, Analyst, Architect, DevOps, QA), ADR-VN-0005:** the entry goes in the **daily file** `Bitacoras/<ROL>/Bitacora-<ROL>-AAAA-MM-DD.md`, with entry ID `<ROL>-AAAAMMDD-HHMM` and the real time, fields Ejecutado, Decisión, Gate, Enlaces and Follow-up. Entries are only appended: never edited or deleted; a correction is a new entry that cites the corrected ID. Check the exact ID prefix in the role's state file (the Architect's says `ARQ-`; the ADR's example for the PM is `PM-`).
     1. Read the day's file and note its hash (size/MD5 from `Fetch_Files_Folders`). Re-read just before writing; if it changed, add your entry after the new ones. If there is no file for today, create it: its first line is the SHA-256 of the previous closed period (take it from the state file's table of closed days).
     2. Show the exact entry, get a yes, then upload (new file, or a new version of the day's file) and verify what was published against what was written (size and MD5).
     3. Rewrite the small **state file** (`Bitacora-<ROL>.md`): the RESUME HERE (keep it short: a pointer to the last entry, not the detail), the pending table (add new follow-ups; when one closes, note why) and nothing else. Upload it as a new version of the same file ID, after re-reading it (it can change during the day), and verify it.
     4. If you are the first agent of the role that day, close the previous day first: append the closing block (entry count, previous day's hash, RESUME HERE snapshot), compute the SHA-256 of the closed file, note it in the state file's table, and review the pending items one by one. A closed file is never modified again.
   - **Dev work in a repository:** the repo's `docs/BITACORA.md` (and `docs/journal/<lote>.md` for a batch) under ADR-VN-0004: mutable RESUME HERE header, append-only entries; the commit cites the story or bug ID (ADR-VN-0002). The WorkDrive and the repo logbooks are independent: cite each from the other's Enlaces field, with the full repository address (URL, branch, commit) so other agents can use it.
   - Never put secrets or personal data in a logbook; link instead of copying.
4. **Hours.** Ask: ¿cuántas horas dedicaste? Propose a figure only as a suggestion. After the user confirms, log them as billable time on the task in Zoho Projects.
5. **Pending or blocker.** If something new appeared, draft it as a task (title, description, role, predecessor, suggested date) and show it. Per the team process the PM registers it: tell the user to notify Danay, or create it only if they explicitly ask.
6. **Task status.** Ask whether to mark the task closed; do not close it silently.

## Ask
- ¿Quedó algo sin terminar que deba ir como pendiente?
- ¿Cambió algún supuesto que afecte otras tareas?
- ¿Las horas son facturables todas?

## If something fails
Zoho/WorkDrive write errors: stop, show the error, keep the prepared text so the user can retry or paste it manually. Never report a write as done without verifying.
