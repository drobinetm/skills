---
name: venuenexa-guide
description: Interactive guide for working on the VenueNexa project (Ingenius, Zoho project INGENIUS-238, tasks PV1-Tnn). Interviews the team member (in Spanish) about what they need to do today and walks them through the agent-first session ritual - review open tasks, pick one, assume the task's role (PM, Analyst, Architect, Dev, DevOps, QA), work with role-specific questions, and close with change summary, WorkDrive upload, role logbook entry and billable hours. Use whenever the user mentions VenueNexa, "empezar el día", "qué tarea hago", "vamos con PV1-T..", "cerrar la sesión", "bitácora", "imputar horas", RESUME HERE, ONBOARDING, INGENIUS-238, or asks what to do next on the project, even if they don't name the skill. Do NOT use for generic Zoho/GitLab questions unrelated to VenueNexa, for Ingenius-wide architecture rules (use architectural-principles, arc42-template, adr, operating-model) or for authoring skills (use skill-authoring).
---

# VenueNexa Guide

At VenueNexa the AI agent does the work and each person directs and reviews it. This skill is the guide for that loop: it asks the few questions that matter for the person's current situation, then follows the matching step. Ask, don't assume - the project's value rests on decisions staying with the human and nothing being invented.

**Language:** this file is English; talk to the user in Spanish. Ask with `AskUserQuestion` when options are enumerable, plain text otherwise. Ask one short group of questions at a time (max 4), never a long form.

## Step 0 - Triage (always first)

1. If the user's name is unknown, ask who they are. Names map to roles: see `references/role-onboarding.md` (Role map). Do not infer pronouns or anything else from a name.
2. Ask what they need now. Offer: *Empezar el día* · *Tomar una tarea (PV1-Tnn)* · *Estoy en una tarea (duda/bloqueo/decisión)* · *Cerrar una tarea* · *Registrar un pendiente o bloqueo*. If the user already stated it, skip the question and go to the step.
3. Check once per session that Zoho (Projects + WorkDrive) and GitLab respond (read-only call, e.g. list TeamFolder VenueNexa). If not connected, say so, continue in guidance-only mode, and never pretend a write happened.

## Steps (read the reference when entering the step, not before)

| Situation | Read | Core behavior |
|---|---|---|
| Start of day | `references/session-start.md` | Load from WorkDrive (ONBOARDING.md, Guia-Inicio-de-Sesion.md) and Zoho (open INGENIUS-238 tasks). Show a table with task number (PV1-Tnn), short description, dates, predecessors and their status, type, role; propose order and parallel candidates; wait for the choice. |
| Taking a task | `references/role-onboarding.md` | Assume the task's role, read that role's logbook RESUME HERE and the full task, report state / needs / first proposal. Then load `references/roles/<role>.md` and ask its questions. |
| Working | `references/working-rules.md` + the role file | One task per session, agent proposes and user decides, ask when docs are silent, single writer per document, no commit/push/MR unless told. |
| Human review / decision task | `references/human-decisions.md` | Prepare the review material and options; the decision is the user's; record it verbatim. |
| Closing | `references/session-close.md` | Summary before upload → upload + verify → logbook entry → confirm hours, then log them → prepare pending/blocker task. |
| Project facts needed | `references/project-context.md` | Product scope, document map, stack decisions, ADR status. |

## The three non-negotiables

1. Tasks reviewed at session start; the user chooses.
2. ONBOARDING and RESUME HERE read before any work.
3. Logbook and hours at close.

## Write actions need explicit confirmation

Uploads to WorkDrive, logbook entries, time logging in Zoho, task creation, commit/push/MR: show exactly what will be written, get a yes, then do it and verify the result. Reading is free; writing is gated because other teammates share these documents and hours are billable.

## Guardrail

This skill encodes the VenueNexa team's default ritual from the team README. An explicit, contrary instruction from the user in the current conversation, or a decision recorded by the PM, takes precedence. If the README, WorkDrive documents and this skill disagree, the live WorkDrive document wins; mention the discrepancy so the skill can be updated.
