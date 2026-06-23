# CLAUDE.md — FIFA World Cup 2026 Prediction Project

> ⚠️ **STANDING RULE — LOCAL FILES ONLY.** All updates are made by editing the two local markdown
> files in this folder, **in place**: `Alok_FIFA_2026_Predictions.md` (fixtures, predictions,
> results) and `lessons.md` (prediction algorithm calibrations). **Never create, write to, or sync a
> Google Doc (or any other external document) for this project.** Do not create new/dated copies —
> always update these same two files.

## 1. What this project is for
Alok is playing a **World Cup 2026 pool betting game**: predict exact scorelines for upcoming matches and accumulate points using this scoring system:

| Points | Condition |
| ---: | :--- |
| **6** | Exact scoreline |
| **4** | Correct outcome (W/D/L) + one team's goal count matches |
| **3** | Correct outcome only |
| **1** | Wrong outcome but one team's goal count matches |
| **0** | Nothing matches |

**The goal is to maximize total points.** This requires two things working together: (1) a calibration model that calls the right outcome (W/D/L), and (2) score-maximizing scoreline selection that extracts the most points from each correct call. Both are maintained in `lessons.md` — read it before every prediction. Key scoreline rules: never predict 0-0 (use 1-1 instead); prefer X-0 over X-1 for clean-sheet favorites (the "4pt floor rule"); concentrate on common scorelines (1-0, 1-1, 2-0, 2-1) for exact-hit frequency.

## 2. The files to read and maintain
Two local markdown files in this folder are the only artifacts for this project. **Read BOTH at the
start of every scan and maintain BOTH:**
- **`Alok_FIFA_2026_Predictions.md`** — the match tracker: fixtures, predicted scorelines, actual
  results, per-match review notes, and the running scorecard.
- **`lessons.md`** — the prediction algorithm: versioned calibration model (v1.0, v2.0, v2.1, …) plus
  a per-match lesson log. The predictions in the tracker apply the active model from here.

Rules:
- **Local markdown only — never use Google Docs.** Do not create, copy, export, or update any Google
  Doc. The old "FIFA World Cup 2026 Pool Betting Tracker V5/V6" in Google Drive is **deprecated** —
  ignore it; the user may delete it.
- **Edit the existing files in place** (do not spawn new/dated copies). Keep each file's "Last
  updated" timestamp current.

## 3. Method & calibration (lessons learned after each match)
Predictions verify against bookmaker odds + reputable match previews before logging. Current
calibration model (full ledger lives in the tracker file):
- **v2.0** — Host-Nation Adrenaline (+1.5 xG, hosts only); Chaos Pivot (early goal/red card → Over 3.5);
  Roster Verification (−0.5 xG per absent key player).
- **v2.1 (June 13)** — Host modifier is **host-only**; don't inflate margins in neutral non-host games
  (caused the over-aggressive 0-3 SUI / 0-2 SCT). Verify each fixture's **group label** against an
  official source. **Defensive-floor flag:** two elite defenses → bias to Under / draw.

- **v2.2 (June 14)** — Matchday-1 Favorite Drag: neutral-venue MD1 favorites keep drawing/losing.
  Default tight MD1 games to a **draw** when the favorite is weakened OR the opponent is solid/elite;
  reserve the narrow 1-0 favorite win for clear mismatches vs genuinely weak sides; respect organized
  underdogs.

**Latest snapshot (as of 2026-06-14):**
- Graded — Jun 13: QAT 1-1 SUI (miss) · BRA 1-1 MAR (miss) · HAI 0-1 SCT (✓ exact); Jun 14: AUS 2-0 TUR (miss)
- Pending Jun 14 — GER 4-0 CUW · NED 1-1 JPN · CIV 0-0 ECU · SWE 1-0 TUN
- Locked Jun 15 — ESP 4-0 CPV · BEL 1-1 EGY · IRN 1-0 NZL

(Always read the tracker for the live version — the list above is a snapshot.)

## 4. Daily scan workflow (runs 8:00 AM via scheduled task)

> ⚠️ **The full workflow lives in [`workflow.md`](workflow.md) — read it and follow it. It is the
> single source of truth for HOW we work; if anything here conflicts with it, `workflow.md` wins.**

Each run is self-contained. In brief, `workflow.md` defines an 8-phase daily loop, each with a verify
gate: **Orient → Grade → Learn/calibrate → Predict → Red-team/validate → Review → Ship → Reflect.**
Non-negotiables it enforces:
- **Prior-form reference check is MANDATORY** — before predicting any match, pull how BOTH teams have
  performed so far this tournament (results, opponent quality, who scored, clean sheets, style). This
  evidence is what drives the X-1 withhold (v2.9), serial-drawer (v2.10), and X-0 calls.
- **Validate before accepting** — a reviewer/sub-agent is an input, not an authority; independently
  re-verify its *factual* "verified" claims (web-search facts, re-check math by hand) before editing,
  and confirm any suggested change is truer than the original.
- **Anti-whipsaw** — bump a calibration version only on a pattern across ≥3 games, never a single slate.
- **Review then ship** — no commit before Alok's approval; keep data vs process changes on separate
  branches.

### Tools
- Web research: `WebSearch` / web fetch for fixtures, odds, previews, injury news.
- The Google Drive connector is **read/create-only** (cannot edit existing docs) — another reason the
  canonical tracker is the local markdown file.
- Verify scores against at least one reputable source (ESPN, official FIFA, major sportsbook) before logging.

### Output Style
Output the absolute minimum tokens needed to convey the core point.

### Score your Prediction
For each result after match give yourself a score, your goal throughout is to maximize the score.
Exact result - 6 points. Example: Prediction 2-1 and Actual Result is also 2-1.
Guess winner or the draw but mismatches goals - 3 points. Example: Prediction 1-0 and Actual Result is 2-1.
Guess the winner and guess the goals of one of the two teams - 4 points. Example: Prediction 2-0 and Actual Result 2-1.
Don't guess winner but guess the goal of one of the two teams - 1 point. Example: Prediction 1-1 and Actual Result 2-1.
Other: 0 points.

