# CAMEL Grant Health Review — Round Protocol

**Goal:** Keep the CAMEL NSF grant on track. Each round identifies the single most
urgent grant health issue — a slipping deliverable, budget divergence, personnel gap,
science blockage, or upcoming reporting requirement — verifies it with evidence from
the repo, and produces a ranked action list for this week. Budget per run: ~$2.

Every wakeup runs **exactly one round** by following these steps in order. This loop
is unattended — favor *verifiable, additive, reversible* actions over clever ones.

## The metric (recompute every round)

Grant health score = count of at-risk or late items across 5 dimensions:

```
timeline_risk    = deliverables with status "at-risk" or "late" AND due within 90 days
budget_risk      = |burn_rate - expected_burn| / expected_burn  (flag if > 15%)
personnel_gap    = any role in STATE.json personnel[] with status != "active" that has open deliverables
science_gap      = deliverables with status "pending" where due is within 60 days
reporting_gap    = reports in STATE.json with submitted=false AND due within 60 days
```

Recompute by reading `STATE.json` at the start of every round. Write the five scores
to the round file. A round may only claim improvement if STATE.json reflects a real
status change made this round.

## Baseline / known failure modes (target these)

- STATE.json is mostly empty at grant start — populate it before the loop is useful.
- Deliverables without due dates cannot be scored — flag them as blockers.
- Meeting notes may contain implicit status changes not yet reflected in STATE.json.
- NSF reporting deadlines can be 60-90 days before the formal anniversary date.

## Hard safety rails (never violate)

1. **Never mutate source grant documents without Becca's confirmation.** The loop
   may *propose* STATE.json changes but not write them autonomously.
2. **Budget guard.** Check `REVIEW_STATE.json → budget.spent_usd_est`. If `>= limit_usd`
   ($2 per run), stop with a final report. This loop does not call paid APIs beyond the
   gate — it reads files. Cost is mainly context tokens.
3. **Evidence before claims.** Do not flag a deliverable as "at-risk" based on a hunch.
   Cite the specific file/field/date that supports the call.
4. **No silent error sinks.** If STATE.json is missing a required field, log the gap
   explicitly; do not skip that dimension.
5. **Do not modify `HYPOTHESES.json` logic, only data** (status flips, posterior updates).

## Round steps

1. **MEASURE.** Read `STATE.json`. Compute the five health scores. Read the most recent
   `grant/meetings/` file. Write scores to `rounds/round_NN.md`.

2. **HYPOTHESIZE — Opus subagent considers, then you take over.** Launch ONE subagent
   with `model: "opus"`, giving it the **pruned `HYPOTHESES.json` view** (frontier nodes +
   posteriors + one-line summaries of dead/exhausted branches — never the whole tree). It
   proposes **3 structurally diverse hypotheses** (one from each of: timeline, budget/personnel,
   science/reporting) about what is most urgent this week, maps each to a tree node, and
   returns a ranked recommendation with evidence needed to verify. ≤250 words.
   Structurally-diverse examples: (A) "D2 is at-risk because owner has no recent activity
   and due date is 45 days out — verify by checking meetings/ for last mention", (B)
   "travel budget is being underspent — flag for reallocation before year-end", (C)
   "Year 1 annual report is due in 8 weeks and no draft exists in reports/".
   **Then YOU (main loop) take over** — the Opus agent only deliberates, it does not execute.

3. **SELECT.** Sanity-check the recommendation against the five health scores and the
   filing. Pick the one hypothesis that, if true and addressed, most reduces grant risk.
   Record the chosen node id + rationale in the round file.

4. **EXECUTE.** Read the specific files needed to verify the selected hypothesis
   (deliverables.md, budget.md, meetings/, reports/). Confirm or refute it. If confirmed,
   draft a specific action item for Becca (e.g., "Schedule check-in with [owner] about D2",
   "Request budget report from grants office", "Open annual report doc and write outline").
   Do NOT autonomously write to grant docs.

5. **VERIFY.** Review the action item: is it specific, actionable, and addressed to the
   right person? Is it based on evidence from the files, not inference? Revise if not.

6. **LOG + PERSIST.** Write back to `HYPOTHESES.json`. Append to `LOG.md`. Update
   `REVIEW_STATE.json`. Call `graph_add_memory` for any confirmed risk. Snapshot
   `rounds/round_NN.md` with: health scores, hypothesis tested, evidence, action item,
   $ this round.

7. **SCHEDULE.** `/loop` re-invokes weekly (or on demand). If a stop condition is met,
   write `FINAL_REPORT.md` and end the loop.

## Context hygiene

- State lives on disk; re-read `PROTOCOL.md` + `STATE.json` + `HYPOTHESES.json` frontier
  fresh each round. Never read the whole hypothesis tree into the main thread.
- Delegate heavy file reading to subagents; return compact summaries only.
- If the round leaves the main context large, `/compact` at the end.

## Stop conditions (any one ends the loop)

- All deliverables have status "done" AND all reports submitted (grant complete).
- `REVIEW_STATE.json → budget.spent_usd_est >= limit_usd` ($2 per run cap).
- Frontier empty / all five mechanism families exhausted (nothing new to hypothesize).
- 4 consecutive rounds with health scores all green and no new evidence of risk.
