# Start of day

Goal: the user knows what is open, what is blocked, and what to take first - without the agent starting anything.

## Do
1. **Load sources first, from both systems.** Do not list tasks before step 2 is done or explicitly marked unavailable.
2. **WorkDrive (TeamFolder VenueNexa):** read `ONBOARDING.md` and `Guia-Inicio-de-Sesion.md`. Load the zoho-mcp skill if installed, otherwise use whatever WorkDrive tool is connected (search tools for "workdrive"). Read live every time; never copy their content into this skill. If no WorkDrive tool exists in the session, say so up front and ask the user to paste or point to the files; never claim to have read them.
3. **Zoho Projects:** portal `ingenius` (id 765280574), project `INGENIUS-238` "Proyecto Venuenexa" (id 1882718000010093270). Verified 2026-10-02:
   - `get_tasks_by_project` with filter `{"criteria":[{"field_name":"status","criteria_condition":"all_open","value":["${all_open}"]}],"pattern":"1"}`, `per_page` 100, `sort_by` `ASC(end_date)`. The response is large (~85k chars) and is saved to a file: query it with `jq`, do not read it whole.
   - The task number is the `prefix` field (e.g. `PV1-T10`). Task names do not contain it.
   - Owners are in `owners_and_work.owners[].name`; match the user's own name.
   - Type and role are in the description text (`Tipo: GENERACIÓN CON AGENTE · rol ...` or `REVISIÓN/DECISIÓN HUMANA`). Strip the HTML.
   - Predecessors are not in the list response. Call `get_task_details` for each of the user's tasks and read `dependency_info.predecessor[].id`, then resolve those ids to `prefix` and `status` from the same list (ids missing from the open list are closed). Descriptions often also name the predecessors; if they disagree with `dependency_info`, trust `dependency_info` and mention it.
4. **Logbooks and logged hours: what was already worked.** Zoho status alone is not enough: a task can be In Review in Zoho while the user's part is already done. Before listing, for each role the user holds (role map in `role-onboarding.md`):
   - Read the logbook live from WorkDrive: the **RESUME HERE** block and the entries dated since the user's last session (or the last 7 days if unknown). Note, per task, what was delivered, decided and left pending.
   - Read the user's time logs from Zoho for the same period (see the lookup note below) to see which tasks already have hours.
   - Cross-check each open task against both. If the logbook and Zoho disagree (e.g. Zoho says open, the logbook says delivered; or hours missing for delivered work), say so and show both; never pick one silently.
   - Local agent work folders and memory may add detail (e.g. `AGENTS/<task>/`, Engram), but the logbook is the source; cite the entry.
   - If the logbook cannot be read, say so and mark every "already done" column as unverified.
5. **Show the list as a table** with, per task: **number (PV1-Tnn)**, **title**, **end date**, **type and role**, **a 1-2 line description** of what it asks (the "Qué:" part of the description, in your own short words, plus the deliverable and where it goes), **predecessors with status** (e.g. `PV1-T10 abierta`), **what the logbook and time logs show already done** (e.g. "comentario publicado, 4:40 h imputadas, espera aprobación de Danay"), and a state: Libre / Bloqueada / Solo revisión / Hecha de tu lado, esperando a X. Keep descriptions short; offer to expand any one on request.
6. Order by end date and dependencies. Tasks already done on the user's side, and blocked tasks, go last, marked "esperando PV1-Txx" or "esperando a <persona>". Never propose as "first" a task whose logbook says the user's part is delivered.
7. Propose what to take first and which can run in parallel, each in its own session.
8. Stop. Do not start any task until the user picks.

## Time-log lookup note (verified 2026-10-07)
Tool `get_time_logs_by_project` (zoho-workdrive MCP, `ZohoProjects_*`) needs `start_date`, `end_date` and `module={"type":"task"}`. **Filtering by a task id (`{"type":"task","id":...}`) returns an empty list even for tasks that have hours** (checked on PV1-T7 and PV1-T10), so never conclude "no hours logged" from it. Query by date range with `{"type":"task"}` and filter by `module_detail.prefix` afterwards. The results show only the connected user's logs; the task's `log_hours` total (from `get_task_details`) may include other people's hours.

## Ask (only what is unclear)
- ¿Con cuál empezamos?
- ¿Tienes algo urgente fuera de Zoho (petición de Danay, bloqueo de otro rol)?
- ¿Cuántas horas tienes hoy? (helps propose how many tasks)
- ¿Quieres llevar alguna en paralelo? If yes, tell them to open another Claude session and run this skill again there.
- For a human-review task: ¿el borrador del agente ya existe en WorkDrive? Check the deliverable path named in the task before asking.

## Edge cases
- No open tasks: say so, ask whether to check blockers or pending items from the logbook (already read in step 4).
- Logbook newer than the user expects (another person wrote an entry on a shared role): show that entry first; single writer per document applies.
- Task has no role or type: flag it as incomplete and suggest asking Danay (PM) to fix it; do not guess.
- Zoho unreachable: ask the user to paste their task list and continue in guidance-only mode.
- Shared tasks (several owners): show all owners, and say which part is the user's if the description splits the work by person.
