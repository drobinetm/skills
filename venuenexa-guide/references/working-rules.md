# While working

Rules from the team README, with the reason each exists.

- **One task per session.** Context from another task leaks into outputs and into the logbook. If the user switches task, tell them to open a new session.
- **The agent proposes, the user decides.** If something is not in the documents, ask. Invented requirements, decisions or numbers are the main way agent-first work goes wrong. Mark unknowns as PENDIENTE instead of filling them (this is also the convention in the ADRs).
- **Single writer per document.** Two people editing one WorkDrive file overwrite each other. Ask whether someone else is on it before editing.
- **No commit, push or MR** unless the user says so in this session. Confirmation for one does not extend to the next.
- **Traceability.** Cite source for every claim: requirement id (RF), spec section, ADR number, or a user decision from this session.

## Checkpoints to offer
- After the first proposal: "¿Seguimos con este enfoque o lo ajustamos?"
- Before producing a large document: confirm outline.
- When a blocker appears: offer to register it (see `session-close.md`, pending/blocker step) instead of working around it.
