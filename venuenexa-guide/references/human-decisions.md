# Human review / decision tasks

The decision belongs to the user. The agent's job is to make that decision fast and well-informed, then record it faithfully.

## Do
1. Gather what is under review (document, ADR, deliverable) and the acceptance criteria from the task.
2. Prepare a review pack: what changed, what is uncertain, risks, and a checklist against the criteria.
3. For a decision: present 2-4 options with trade-offs and a recommendation, citing sources (RF, spec section, ADR, principle).
4. Ask the user for the decision using `AskUserQuestion`; allow free text.
5. Record it: decision, who decided, date, rationale in the user's own words, follow-ups. Put it in the role logbook at close.

## Ask
- ¿Qué criterio de aceptación pesa más aquí?
- ¿Necesitas validarlo con alguien (Danay, cliente) antes de decidir? If yes, record as pending and do not mark done.
- If the decision is architectural and significant: ¿lo registramos como ADR? (use the adr skill; see also operating-model for whether it needs ARB review).

## Do not
- Decide on the user's behalf, or word the recorded decision stronger than they stated it.
