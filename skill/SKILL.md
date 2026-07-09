---
name: nsf-grant
description: Use when Becca asks about the CAMEL NSF grant — what's due, deliverable/milestone status, budget, personnel, what was decided about X, processing meeting notes or voice captures into the grant repo, or recording a decision. Triggers: "camel", "the NSF grant", "what's due on the grant", "grant status", "add this to the grant repo".
---

# CAMEL Grant Brain

## Overview

This skill is the administrative brain for the CAMEL NSF grant (Award #2621173).
Structured status lives entirely in a git repo — there is no separate OneDrive source
for this one (unlike GPO).

**Repo:** `/Users/becca/Code/admin/grants/camel` (GitHub `rkn2/camelPSU`)

**Canonical copy:** `~/Code/admin/grants/camel/skill/SKILL.md` — edit this one, commit, push.
**Installed copy:** `~/.claude/skills/nsf-grant/SKILL.md` — after editing canonical, copy it here too
(mirrors the GPO skill's canonical/installed split). Never edit the installed copy directly.

---

## Step 1: Sync the repo

```bash
cd /Users/becca/Code/admin/grants/camel && git pull
```

Always do this before answering — the repo may have been updated from another machine or session.

---

## Step 2: Route the query

| Question | Read first | Then |
|----------|-----------|------|
| What's due / what am I behind on? | `STATE.json` → `deliverables[]` | `grant/milestones.md` |
| What should I focus on this week? | `STATE.json` | Most recent `grant/meetings/` file |
| What was decided about X? | `decisions/` (search by topic) | Relevant `grant/meetings/` file |
| Budget status? | `grant/budget.md` | `STATE.json` → `budget` |
| Who is responsible for X? | `STATE.json` → `deliverables[].owner` | `grant/personnel.md` |
| What's the grant scope / aims? | `grant/overview.md` | NSF award documents in `reports/` |
| What code supports X? | `code/notebooks/` or `code/telemetry/` | README in that subdir |

## Key file roles

- **`STATE.json`** — machine-readable source of truth for all deliverables, milestones, personnel, budget. Updated whenever a status changes. Always report its `last_updated` date alongside any answer drawn from it.
- **`grant/meetings/YYYY-MM-DD-topic.md`** — one file per meeting. Most recent = most current context.
- **`decisions/YYYY-MM-DD-decision-title.md`** — one file per significant decision. Institutional memory.
- **`grant/deliverables.md`** — full narrative description of each deliverable (more detail than STATE.json).
- **`HYPOTHESES.json` + `PROTOCOL.md`** — drive the `/loop`-based weekly grant health review. Do not modify these outside of running that loop.

---

## Key grant facts (orientation only)

These are handy for quick recall, but **STATE.json and the repo are the source of truth** —
if either disagrees with this section, trust them and flag the discrepancy to Becca so this
section can be updated.

- NSF Award #2621173, $1,508,507 total — "Phase I CAMEL-CN: Modeling the Messy"
- PI: Rebecca (Becca) Napolitano. Co-PIs: Yao, Reinhart, Zuo, Hill
- NSF award period: 07/01/2026–06/30/2029
- Practical start: Jan 1, 2027 — Jul–Dec 2026 is setup only, **no charges** against the budget
- 3 internal orders (IOs): PSC (participant costs), AE Engineering (Becca runs), Education (Kathy Hill runs)
- All travel routes through the Engineering IO
- Tuition remission split: 1 student on Engineering IO, 1 student on Education IO
- NSF Program Officer: Elizabeth Chua, echua@nsf.gov
- NSF Grants Official: Tyffani Smith, tnsmith@nsf.gov

## Standing watch items

Surface these whenever relevant, even if not directly asked:

- **IRB not yet approved.** No human-subjects work (recruitment, data collection) can start until
  it is. This blocks most Year-1 activity — check `STATE.json` → `irb` before telling Becca
  something is on track if it touches students, teachers, or data collection.
- **Annual RPPR reports** are typically due to NSF within the 90 days *before* each award
  anniversary. Exact dates must be confirmed on research.gov, then recorded in
  `STATE.json` → `reports`. If a report deadline is coming up and `reports.*.due` is still
  a placeholder/unconfirmed, flag that explicitly rather than treating it as final.

---

## Step 3: Processing meeting notes or voice captures

When Becca provides meeting notes or a voice capture to log:

1. Format into `grant/meetings/YYYY-MM-DD-topic.md`.
2. Flag any deliverable status changes (e.g., on-track → at-risk, or → done).
3. Extract decisions and ask whether each should also go to `decisions/`.
4. Propose the `STATE.json` diff and show it to Becca before writing.

## Step 4: Recording a decision

Create `/Users/becca/Code/admin/grants/camel/decisions/YYYY-MM-DD-topic.md`:

```markdown
# <Topic> — <Date>

**Decision:** <one-sentence ruling>

**Context:** <why this came up, who was involved>

**Outcome:** <what was decided and how to apply it going forward>
```

## Write procedure

After any write to the repo (STATE.json diff, new meeting file, new decision, budget/personnel
edit), commit with a descriptive message and push:

```bash
cd /Users/becca/Code/admin/grants/camel
git add <files>
git commit -m "<what changed and why>"
git push
```

---

## Other grants

`~/Code/admin/grants/` also holds `cir/`, `eci/`, and `template/` — none of these are wired up
to this system yet. If Becca asks about CIR or ECI, say so plainly rather than guessing from
this skill, and offer to set one up from `template/` if she wants.
