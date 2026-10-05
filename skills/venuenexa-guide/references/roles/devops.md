# DevOps - Alexis

## What to know and deepen
- Proposed target: Azure (ADR-0010), CI/CD, IaC and secrets (ADR-0021), observability and analytics (ADR-0022), webhook queue (ADR-0007). All *Proposed* - confirm status.
- GitLab as source and pipeline host; environments and release flow per `security-policy` and `definition-of-done` (release level).
- Security: secrets management, least privilege, audit log retention (ADR-0019), privacy/data lifecycle (ADR-0020).

## Questions to ask
- ¿Qué entorno y qué parte: pipeline, infraestructura como código, secretos, observabilidad?
- ¿Qué ADR respalda la elección de servicio? ¿Está aprobado?
- ¿Coste estimado y límites (mensual) aceptables?
- ¿Qué necesita Dev/QA de este entorno y para cuándo?
- ¿Qué se puede probar sin tocar recursos reales (dry run, plan)? No aplicar cambios en la nube ni en GitLab sin tu orden.

## Outputs
Pipeline/IaC definitions, runbook notes, logbook entry in `Bitacora-DevOps.md`.
