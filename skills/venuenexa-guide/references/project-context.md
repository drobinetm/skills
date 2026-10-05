# VenueNexa project context

Facts verified from the local project folder on 2026-10-02. Check dates before relying on version-specific details; live WorkDrive documents win.

## Product
Two-sided booking marketplace ("Airbnb for wedding and event venues"). Guests discover, tour, book and pay venues; owners publish venues and manage calendar, tours, bookings and payouts. Bilingual (EN/ES) AI search agent. Platforms: responsive web, native iOS, native Android (no native macOS).
Roles in the product: Visitor, Guest, Owner-org admin, Venue manager, Venue staff, Platform support, Moderator, Platform admin. Least privilege, venue-scoped access; sensitive actions need step-up auth and immutable audit logs.
Core rule: a booking is not confirmed until contract acceptance and payment authorization/capture succeed; double bookings must be prevented (holds, transactional rules).
Out of scope for launch: full event planning/vendor marketplace, ticketing, native macOS, dedicated iPad UI, accounting/payroll, automated legal-compliance determination.

## Document map (local folder `VENUENEXA/`)
| Item | Use |
|---|---|
| `VenueNexa_Requisitos_y_Especificacion_del_Sistema_ES.docx` / `Venue_Marketplace_Product_Requirements_and_Specification.docx` | Product spec v1.3 (ES / EN): scope, roles, flows, success metrics |
| `Propuesta_Desarrollo_VenueNexa_28_08_26_v2.pdf` | Commercial proposal |
| `Estimación - Proyecto VenueNexa Act.xlsx` | Effort estimate |
| `ARQUITECTURA/` | Analyses: e-signature, age verification/KYC, Firebase vs specialized services, integration tools, Mux vs CloudFront, architecture audio |
| `backend-prueba/` | Backend proof of concept; `docs/adr/` has ADR-0001..0030 (all *Proposed*) and `REVIEW-2026-09-29.md` listing pending ADRs |

Requirements matrix referenced by the ADRs: 122 functional requirements (RF), 13 epics.

## Stack decisions in the ADRs (all Proposed, not final)
.NET 8 modular monolith, PostgreSQL (geospatial search), REST/OpenAPI, Keycloak (OIDC/OAuth2), Azure cloud, Azure OpenAI for the AI agent, Next.js + Refine (admin), Flutter (mobile), Stripe Connect payments, Twilio SMS, Firebase FCM push, Mux video, xUnit tests, arc42 docs. Treat these as proposals when talking to the user; check the ADR status before stating one as decided.

## Team process
Zoho Projects project `INGENIUS-238`; tasks `PV1-Tnn`; WorkDrive TeamFolder `VenueNexa` with ONBOARDING.md, Guia-Inicio-de-Sesion.md and per-role logbooks; GitLab for code. Ingenius marketplaces installed: governance-skills and sdlc-skills.
