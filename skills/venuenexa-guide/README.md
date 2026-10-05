# Skill: `venuenexa-guide`

Guía interactiva para trabajar en el proyecto VenueNexa (Ingenius, Zoho INGENIUS-238, tareas PV1-Tnn). Entrevista a la persona (en español) y la lleva por el ritual de sesión "agent-first": revisar tareas abiertas, elegir una, asumir el rol de la tarea (PM, Analyst, Architect, Dev, DevOps, QA), trabajar con preguntas propias del rol y cerrar con resumen de cambios, subida a WorkDrive, entrada de bitácora e imputación de horas.

## Instalar

```bash
cp -r skills/venuenexa-guide ~/.claude/skills/
```

Requiere conexión a Zoho (Projects + WorkDrive) y GitLab; sin ellos funciona en modo solo-guía.

## Contenido

- `SKILL.md` — triage inicial, tabla de pasos y reglas no negociables.
- `references/session-start.md`, `role-onboarding.md`, `working-rules.md`, `human-decisions.md`, `session-close.md`, `project-context.md` — se leen al entrar en cada paso.
- `references/roles/` — preguntas y contexto por rol (pm, analyst, architect, dev, devops, qa).
- `evals/evals.json` — casos para medir la fiabilidad del disparo.
- `DECISIONS.md` — registro de decisiones de diseño del skill.

## Cuándo no usarlo

Preguntas genéricas de Zoho/GitLab ajenas a VenueNexa, o reglas de arquitectura de Ingenius (usar `architectural-principles`, `arc42-template`, `adr`, `operating-model`).
