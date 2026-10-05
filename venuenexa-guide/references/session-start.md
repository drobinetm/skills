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
4. **Show the list as a table** with, per task: **number (PV1-Tnn)**, **title**, **end date**, **type and role**, **a 1-2 line description** of what it asks (the "Qué:" part of the description, in your own short words, plus the deliverable and where it goes), **predecessors with status** (e.g. `PV1-T10 abierta`), and a state: Libre / Bloqueada / Solo revisión. Keep descriptions short; offer to expand any one on request.
5. Order by end date and dependencies. Blocked tasks go last, marked "esperando PV1-Txx".
6. Propose what to take first and which can run in parallel, each in its own session.
7. Stop. Do not start any task until the user picks.

## Ask (only what is unclear)
- ¿Con cuál empezamos?
- ¿Tienes algo urgente fuera de Zoho (petición de Danay, bloqueo de otro rol)?
- ¿Cuántas horas tienes hoy? (helps propose how many tasks)
- ¿Quieres llevar alguna en paralelo? If yes, tell them to open another Claude session and run this skill again there.
- For a human-review task: ¿el borrador del agente ya existe en WorkDrive? Check the deliverable path named in the task before asking.

## Edge cases
- No open tasks: say so, ask whether to check blockers or pending items from the logbook.
- Task has no role or type: flag it as incomplete and suggest asking Danay (PM) to fix it; do not guess.
- Zoho unreachable: ask the user to paste their task list and continue in guidance-only mode.
- Shared tasks (several owners): show all owners, and say which part is the user's if the description splits the work by person.
