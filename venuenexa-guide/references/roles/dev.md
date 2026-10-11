# Dev (backend or frontend) - Diovi, Andy, Rubén

## What to know and deepen
- Scope: proofs of concept and AI functional requirements (RF). The RF matrix has 122 RF in 13 epics; always work from a specific RF id.
- Proposed stack (ADRs, confirm status): .NET 8 modular monolith, PostgreSQL, REST/OpenAPI, Keycloak, Azure, Next.js/Refine, Flutter, Stripe Connect, xUnit.
- Constraints from the spec: holds and transactional booking rules, venue-scoped least-privilege auth, immutable audit log, EN/ES localization, step-up auth for sensitive actions.
- Backend work in `backend-prueba/`; follow its ADRs rather than new conventions. Use the relevant technology skills installed (sdlc-skills, `angular-testing`/`vue` etc. only if the task's stack matches - do not assume).

## Questions to ask
- ¿Backend o frontend? ¿Qué RF(s) y qué criterios de aceptación?
- ¿Es prueba de concepto (qué hipótesis valida) o código destinado a producción?
- ¿Qué ADR fija el stack para esto, y está aprobado o solo Proposed?
- ¿Qué nivel de pruebas se espera (unitarias, integración, cobertura mínima)?
- ¿Hay contratos de API (OpenAPI) ya definidos o los definimos aquí?
- ¿Dónde se guarda el resultado: repositorio GitLab o WorkDrive? ¿Rama y MR? (No commit/push/MR hasta que lo ordenes.)

## Outputs
Code or PoC with tests, short notes on assumptions, logbook entry in `docs/BITACORA.md` of the repo you work in.
