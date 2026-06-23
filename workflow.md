# workflow.md — Standard Agent Workflow (FIFA WC 2026 Prediction Project)

> **This file is the single source of truth for HOW every agent works on this project.**
> `CLAUDE.md` defers to this file for the workflow; if the two ever conflict, **`workflow.md` wins** —
> fix `CLAUDE.md` to match. `lessons.md` holds the prediction *model*; this file holds the *process*.

## 0. The goal & the two loops
Maximize the pool score by getting better **every day**. "Better" runs on two nested loops, plus one
stabilizer that stops them eating themselves:

- **Inner loop — the model.** predict → grade → lesson → calibrate → predict better. Lives in
  `lessons.md`. Improves the *picks*.
- **Outer loop — the process.** work → catch a process failure → encode a rule → work better. Lives in
  this file, `CLAUDE.md`, and memory. Improves the *agent*. (Example: the validate-before-accepting
  rule in Phase 5 came from a process failure, not a model error.)
- **Stabilizer — anti-whipsaw.** The known failure mode is over-fitting to 1–4 game samples (we bumped
  v2.2→v2.7 in a week, each chasing the last result). **Improve on sustained patterns, not single
  slates.** A confirming slate is NOT a reason to change anything.

## 1. The daily loop (8 phases — each has a verify gate; do not advance until it passes)

### Phase 1 — Orient
Read this file, then `Alok_FIFA_2026_Predictions.md` and `lessons.md` in full. Know before you act:
the active model version, the pending fixtures, the current **#1 recurring error**, and the standing
and gap to the leader.
**Verify:** you can state today's single biggest leak in one sentence.

### Phase 2 — Grade finished matches
Web-confirm every final score from **≥2 reputable sources** (ESPN, official FIFA, a major sportsbook)
before logging. Fill the "Actual Result" column, mark Win / Miss / Win (wrong margin), score each per
the rubric (§3), and update the scorecard.
**Verify:** every score is sourced from ≥2 places and all scorecard arithmetic is re-checked by hand.

### Phase 3 — Learn & calibrate (disciplined)
Add a one-line takeaway per graded match to the `lessons.md` log. **Separate signal from noise:** a
pattern is only durable if it holds across **≥3 games**; a single-game result is variance (e.g. a
red-card 0-0) until proven otherwise. **Bump a calibration version only on a sustained pattern** — and
explain the adjustment. On a confirming slate, log the validation and change nothing.
**Verify:** any new version cites ≥3 supporting games; you consciously resisted a single-slate whipsaw.

### Phase 4 — Predict the next 24h
1. Find every WC 2026 fixture in the next 24h (delegate to the **`find-schedules`** subagent, defined
   at `.claude/agents/find_schedules/find_schedules.md`). The subagent is scoped to a single calendar
   date, so when the 24h window crosses midnight in your declared timezone, **run it for each date the
   window spans (typically today + tomorrow) and merge the results** — then **verify each fixture's
   group** against an official source.
2. **MANDATORY — Prior-form reference check (do this for BOTH teams, every match).** Pull how each
   team has performed *so far this tournament* and in recent relevant matches — this is a required
   input, not optional color:
   - Their results to date: scoreline, **opponent quality**, how they won/lost, goals for/against,
     clean sheets, and **who scored**.
   - Style signals revealed by those games: did they bunker or come out to play, do they leak, do they
     convert chances, is there a key man they depend on (and is he fit)?
   - This directly drives the model: a **"demonstrated goal" this tournament** is what triggers the
     v2.9 X-1 withhold; a **serial-drawer / wasteful** pattern triggers v2.10; a **leaky/open** vs an
     **organized low-block** opponent is the X-0-vs-not call. You cannot make these calls without the
     prior-match evidence — so gather it first.
   *(Reminder of the trap: judge an opponent's threat against THIS favorite's defence and form, not
   transitively against a common third team — see the ARG/Austria lesson.)*
3. Pull current **odds + team news** (injuries, lineups, must-win situations).
4. Apply the model from `lessons.md`: **North Star first — call the outcome (W/D/L)**, then pick the
   score-maximizing scoreline (never 0-0; X-0 floor for clean-sheet favorites; common scorelines for
   exact hits; lift margins per v2.7).
**Verify:** every pick has (a) a logged prior-form line for both teams, (b) an outcome rationale stated
*before* the scoreline, (c) a verified group label.

### Phase 5 — Red-team / self-verify (validate before accepting)
Run an adversarial pass over your own grades and picks (a sub-agent red-team is encouraged for full
slates). **A reviewer — human or sub-agent — is an input, not an authority.** Independently re-verify
its high-stakes *factual* claims, not just its opinions: web-search facts against a reputable source,
re-check arithmetic by hand. When a critique tells you to **change** existing text, first confirm the
new claim is actually **truer** than the old one — never "upgrade" accurate wording into an
overstatement.
**Verify:** every accepted change is independently confirmed and is truer than what it replaced.

### Phase 6 — Review with the human
Notify Alok with a short summary (graded results + points, new picks + rationale, standing). Get
approval.
**Gate:** no commit before approval and score-status agreement.

### Phase 7 — Ship
Branch per the `claude/<short-desc>` convention, commit, push, open a PR. **Keep prediction-data
changes and process/doc changes on separate branches** (don't bundle `lessons.md`/tracker edits with
`CLAUDE.md`/`workflow.md` edits).
**Verify:** branch named to pattern; PR body summarizes what changed and why.

### Phase 8 — Reflect (meta-improvement)
Capture **process** lessons (not just prediction lessons) to memory and, when they're standing rules,
to `CLAUDE.md`/this file — so the way we work improves, not only the model.

## 2. Leverage points (where a small shift → a big gain)
- **Outcome accuracy (North Star).** Flipping one outcome wrong→right ≈ **+3 pts**; refining a
  scoreline ≈ **+0.5–1**. Always fix the outcome first.
- **Convert correct outcomes → exacts.** This is the current frontier (the floor logic is solved).
- **Protect the grade→lesson loop from whipsaw.** The loop is the engine; the discipline is what keeps
  it from over-fitting itself into noise.

## 3. Scoring rubric
The scoring table is **canonical in [`CLAUDE.md`](CLAUDE.md) §1** — read it there (6 = exact · 4 =
correct outcome + one team's goal count · 3 = correct outcome only · 1 = wrong outcome + one goal
count · 0 = nothing). Kept in one place to avoid the two copies drifting.

## 4. Daily success metrics (so "better" is measurable)
Track the trend, not just the day: **pts/match** (target ≥ 3.0), **outcome-accuracy %**,
**exact-hit rate**, and **gap to the leader**.

## 5. Hard constraints
- **Local markdown only — never Google Docs.** Edit `Alok_FIFA_2026_Predictions.md` and `lessons.md`
  in place; never spawn dated copies. Keep both timestamps current.
- **Verify before logging.** Scores from ≥2 reputable sources; facts and math independently checked
  (Phase 5).
