# Taking a task

## Role map (from the team README; confirm with the task, which is authoritative)

| Person | Role(s) | Logbook: state file · daily entries (WorkDrive, TeamFolder VenueNexa) | Role file |
|---|---|---|---|
| Danay | PM / Tech Lead | `Bitacora-PM.md` · `Bitacoras/PM/` | `roles/pm.md` |
| Yaimelys | Analyst | `Requirements/Bitacora-Analista.md` · `Bitacoras/Analista/` | `roles/analyst.md` |
| Diovi, Andy | Architect (arc42) | `Architecture/Bitacora-Arquitecto.md` · `Bitacoras/Arquitecto/` | `roles/architect.md` |
| Diovi, Andy, Rubén | Dev backend or frontend (proofs of concept, AI RF) | `docs/BITACORA.md` of the repo you work in (`api`, `web`, `android`, `ios` or `poc`) | `roles/dev.md` |
| Rubén | Architect (AI proposal) | `Architecture/Bitacora-Arquitecto.md` · `Bitacoras/Arquitecto/` | `roles/architect.md` (AI section) |
| Alexis | DevOps | `Bitacora-DevOps.md` · `Bitacoras/DevOps/` | `roles/devops.md` |
| Danaysa | QA | `Bitacora-QA.md` · `Bitacoras/QA/` | `roles/qa.md` |

The role comes from the Zoho task, not from the person: a person with several roles works the one the task names.

## Do
1. Confirm the task id (PV1-Tnn) and open it in Zoho; read the full task (description, predecessors, type, deliverable).
2. Assume the task's role. Read that role's state file (its **RESUME HERE** and pending table) and its latest daily file in `Bitacoras/<ROL>/`; for Dev work, the repo's `docs/BITACORA.md` header.
3. Report to the user in Spanish: current state, what you need to start (inputs, access, decisions), what you propose to do first.
4. Load `roles/<role>.md` and ask the relevant questions before producing anything.
5. If the task type is HUMAN REVIEW/DECISION, switch to `human-decisions.md`.

## Ask
- ¿Trabajas esta tarea como <role de la tarea>? (when the person has several roles)
- ¿Hay algo que ya hayas avanzado fuera de la bitácora?
- Anything the role file lists as required input that is missing.

## Edge cases
- RESUME HERE missing or stale: tell the user, offer to reconstruct it from the daily files (the state file is rebuildable from them), and ask them to confirm before relying on it.
- Another person is editing the same document: stop, tell the user, wait (single writer per document).
