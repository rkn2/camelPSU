# Grant Query Guidance (CAMEL Grant)

This repo is the administrative brain for the CAMEL NSF grant. Full query-routing rules and
procedures (deliverable/status lookups, budget, decisions, meeting-note processing, write
procedure) live in `skill/SKILL.md`, installed as the **nsf-grant** Claude Code skill — use
that skill rather than duplicating its logic here.

## Repo-structure conventions

These apply to anyone working in this repo, skill or no skill:

- **`STATE.json`** — machine-readable current status of all deliverables, milestones, personnel, budget. Updated whenever a status changes. Always include `last_updated` date when reporting.
- **`grant/meetings/YYYY-MM-DD-topic.md`** — one file per meeting. Most recent = most current context.
- **`decisions/`** — one file per significant decision: `YYYY-MM-DD-decision-title.md`. Institutional memory.
- **`grant/deliverables.md`** — full narrative description of each deliverable (more detail than STATE.json).
- **`HYPOTHESES.json` + `PROTOCOL.md`** — drive the `/loop`-based weekly grant health review. Do not modify unless running the loop.
