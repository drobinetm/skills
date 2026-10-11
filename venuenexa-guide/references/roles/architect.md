# Architect (arc42) - Diovi, Andy; AI proposal - Rubén

## What to know and deepen
- arc42 structure for this project (use the `arc42-template` skill); the architecture documentation lives in WorkDrive `Architecture/`.
- ADR format (`adr` skill) and the existing ADR-0001..0030 in `backend-prueba/docs/adr/`, all *Proposed*; `REVIEW-2026-09-29.md` lists pending ADRs.
- Ingenius principles P01-P16 (`architectural-principles`) and when a decision needs ARB review (`operating-model`).
- Analyses in `ARQUITECTURA/` (e-signature, KYC/age verification, Firebase vs specialized, integrations, Mux vs CloudFront).
- Key forces: double-booking prevention, payments (Stripe Connect), multi-tenancy/authorization, bilingual EN/ES, privacy and audit log, Azure hosting.
- AI proposal (Rubén): ADR-0003 and ADR-0017; apply `responsible-ai` (risk level, controls for RAG/prompt injection/hallucination/cost/provider dependency) and `per-modality-checklist`.

## Questions to ask
- ¿Qué sección de arc42 o qué ADR cubre esta tarea? ¿Es nuevo o revisión de uno Proposed?
- ¿Qué atributos de calidad mandan aquí (consistencia de reservas, seguridad, coste, latencia)?
- ¿Cuáles son las alternativas ya descartadas y por qué?
- ¿Hay requisitos (RF) o secciones del spec que justifiquen la decisión? ¿Qué campos quedan PENDIENTE?
- ¿Afecta a otro rol (Dev, DevOps, QA)? ¿Requiere pasar por ARB?
- (AI) ¿Qué nivel de riesgo tiene este caso de uso y qué evidencia mínima exige?

## Outputs
Updated arc42 sections, ADR drafts with every field filled or marked PENDIENTE, logbook entry in today's file of `Bitacoras/Arquitecto/` and the state file `Architecture/Bitacora-Arquitecto.md`.
