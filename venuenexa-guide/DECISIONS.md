# Decision log - venuenexa-guide

| ID | Date | Decision | Justification | Verified |
|---|---|---|---|---|
| D-01 | 2026-10-02 | Personal skill at `~/.claude/skills/venuenexa-guide/`, not an Ingenius marketplace plugin | User choice; fastest to iterate | n/a |
| D-02 | 2026-10-02 | One skill covers all roles, with per-role files under `references/roles/` | User choice; loads only the needed role file, keeping one objective (guide a session) | n/a |
| D-03 | 2026-10-02 | Skill content in English, conversation with the user in Spanish | Ingenius English-content standard; team works in Spanish | n/a |
| D-04 | 2026-10-02 | Use Zoho/WorkDrive/GitLab directly when connected; every write needs explicit confirmation | User choice; hours are billable and documents are shared | n/a |
| D-05 | 2026-10-02 | Documents in WorkDrive (ONBOARDING, Guia, logbooks) are read live, never copied | They change; copies would go stale | README only; WorkDrive not yet read |
| D-06 | 2026-10-02 | Role-to-person map and logbook paths taken from the team README | Only source available | Not checked against WorkDrive |

| D-07 | 2026-10-02 | Task listing always shows PV1-Tnn number and a short description; sources are loaded from both WorkDrive and Zoho before listing | User feedback after first run | Yes: `prefix` field holds the number; `get_task_details.dependency_info` returns predecessors (checked on PV1-T7: 6 predecessors, matches description) |
| D-08 | 2026-10-07 | Start of day reads the user's role logbooks (RESUME HERE and recent entries) and logged hours before listing tasks, and shows what is already done per task | In a real session the skill proposed PV1-T10 first although the logbook and time logs showed the user's part delivered; logbooks were read only after a task was chosen | Yes: `get_time_logs_by_project` with a task-id filter returns empty for PV1-T7 and PV1-T10 (both have hours); date range plus `{"type":"task"}` returns them |

## Open verification
- Zoho Projects lookup of INGENIUS-238 works (portal 765280574, project 1882718000010093270). No WorkDrive tool was available in the session that tested it: WorkDrive loading is still unverified.
- Eval 4 (start of day with logbook cross-check) added 2026-10-07; not yet run.
- Trigger reliability not yet measured (needs the description eval loop).
