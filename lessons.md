# lessons.md — Prediction Model for the KNOCKOUTS (Round 2+)

_Active calibration for the **knockout rounds** (Round of 32 onward). Round 1's full ledger + retrospective is archived in **`round1_lessons.md`** — read it once for context. The scoring is the **same as the group stage**; what changes is the game dynamics: **every match is win-or-out, both teams trying** (no dead rubbers / content-favorites / motivational rotation — though teams still rotate for injuries/suspensions)._

**Last updated:** 2026-07-01 — **R32 through Jun 30: RSA ✓6, BRA ✓6, CIV ✓6 (3 exacts); MEX-ECU 4; FRA-SWE 3; GER-PRY 0; NED-MAR 0 (not submitted). Cumulative 213** (188 group + 25 knockout). 7 R32 games done, 9 remaining. Jul 1 picks (ENG-COD 2-1, BEL-SEN 2-1, USA-BIH 2-1) submitted + reload-verified. _(FRA 3-0 SWE: the "withhold X-0 for Isak/Gyökeres" was over-cautious vs a -400 steamroller — see lesson log.)_

---

## 🎯 KNOCKOUT SCORING — same 6/4/3/1/0 (confirmed on the Pollaya `/puntos` page + by Alok)
**The point system is identical to the group stage** — correct outcome (W/D/L) +3 (the Pollaya page labels this "Winner selection"), each team's goal-count +1, exact +1 bonus, which sum to the familiar tiers:
- **6** = exact scoreline · **4** = correct outcome + one team's goal count · **3** = correct outcome only · **1** = wrong outcome + one team's goal count · **0** = nothing.
- Separate **one-time** tournament bonuses (not per-match; locked pre-tournament, confirmed on the Pollaya `/puntos` page): **pick the champion +10, pick the runner-up +10.**

**The ONLY knockout difference — penalties:** a match is scored on its **90/120-minute result**. **Penalties are excluded** → a tie that's level after extra time is scored as a **DRAW**, and predicting the shootout winner earns **nothing**. So predict the result *within* 90/120 minutes.
- _Check (actual 1-1, won on pens): predict 1-1 → 6; 0-0/2-2 → 3 (correct outcome only); 1-0/2-1 → 1; 2-0 → 0. (**4** is impossible vs a draw — a draw prediction matches both goals → 6, or neither → 3, never exactly one.)_

---

## ⭐ NORTH STAR (same model as the group stage — it's the same scoring)
1. **Outcome first, then scoreline.** Correct W/D/L is a guaranteed 3 and the gateway to 4/6; wrong outcome caps at 1. Fix the outcome, then optimize the score.
2. **Back the bookmaker favorite** to win unless a concrete, verified reason says otherwise.
3. **Predict the single most-likely (modal) scoreline.** Concentrate on **common scores (1-0, 2-1, 1-1, 2-0, 0-1)**; **never 0-0 → use 1-1**.
4. **X-0 floor** for a clear favorite likely to keep a clean sheet (the 4-pt floor rule).
5. **For two even, organized sides → predict the 1-1 draw.** A knockout tie counts as a *draw* (penalties excluded), so 1-1 is a real, scoring pick — **never predict the penalty winner.** Jun 28 proved we can call draws (ALG-AUT 3-3, COL-POR 0-0 both hit).
6. **Don't over-inflate margins.** Knockouts are cagier/lower-scoring than group blowouts; the modal favorite win is usually **1-0 / 2-1 / 2-0**, not 3-1. Back a big margin only in a genuine mismatch.

## Knockout regime notes (what's different — it's the game, not the scoring)
- **No dead rubbers / content favorites / motivational rotation** — every game is win-or-out, both trying, so R1's biggest leak (favorites coasting in low-stakes games, the v2.12 motivation-mismatch) is **gone** — don't apply those overrides here. *(Teams still rotate for injuries/suspensions/tactics — always run the lineup & availability check.)*
- **Cagier, lower-scoring** → favor 1-0 / 2-1 / 1-1; fewer blowouts.
- **Genuine mismatch** (group winner vs a 3rd-place qualifier) → back the favorite with a clean decisive score (often X-0). **Two evenly-matched sides** → 1-1 is live (and a tie is scored as a draw).

## Operational (hard rule)
- **Validate every load-bearing claim** (form, injuries, a cited result) *including its context* before locking a score (see workflow Phase 4).
- **After generating picks: list them for Alok, enter on the app, and RELOAD-VERIFY each is saved.** R1 lost ~5 pts to two un-submitted picks. The app is the source of truth for schedule + scoring.

---

## Lesson log — Knockouts (per-match takeaways)
| Date | Match | What we learned |
| :--- | :--- | :--- |
| Jun 28 | RSA 0-1 CAN | **Exact (6) — 1st knockout game.** The X-0 floor read held: a clear favorite (Canada -140, home) to nil vs a toothless side (SA ≤1 goal/game) = the 6. **Confirms the group 6/4/3/1/0 model transfers directly to knockouts** (same scoring). Late winner (90+2') but the margin stayed at 1, as the Davies-out cap implied — don't over-inflate favorite margins in cagey knockouts. |
| Jun 29 | BRA 2-1 JPN | **Exact (6) — 2nd straight.** Full-strength favorite + a weakened opponent that still scores → the modal 2-1. Brazil trailed 0-1 at half then won late (Martinelli 90+5') — backing the favorite held through the scare. The modal-scoreline knockout model is working. |
| Jun 29 | GER 2-0 PRY | **Miss (0): the 2-0 was too rich.** Germany (heavy fav) only drew a Gómez-less Paraguay 1-1 (pens). Backing Germany wasn't wrong, but the X-0/2-0 margin over-reached for a cagey knockout. **With NED-MAR also 1-1, two of the day's knockouts went to pens → R32 is draw-heavy: favor 1-0/1-1 over 2-0, respect the draw on tight ties.** |
| Jun 29 | NED 1-1 MAR | **PROCESS miss (0 — not submitted).** Paused at 99% quota; the deferred resume landed after the lock → blank. **Hard operational rule: enter every same-day game EARLY (well before the ~15-min lock); a quota pause must never overshoot a kickoff.** This is the R1 un-submitted leak resurfacing — guard it. |
| Jun 30 | CIV 1-2 NOR | **Exact (6) — 3rd R32 exact.** The X-0 withhold was the right call: Norway won 2-1, CIV nicked one. "Withhold X-0 for a leaky D" (7 conceded) = correct; also validates the draw-or-tight-win read on sub-favorites. |
| Jun 30 | FRA 3-0 SWE | **Partial (3 — outcome only): over-cautious X-0 withhold.** France was -400 and blew Sweden out 3-0. We predicted 2-1 to "leave room for Isak/Gyökeres" but France dominated (12 shots on target — their most in a WC knockout since 1966) and kept the clean sheet. **Rule: for a -350+ steamroller vs a weak opponent, default X-0 unless the opponent has a live striker confirmed in XI.** Isak/Gyökeres hype ≠ concrete threat. |
| Jun 30 | MEX 2-0 ECU | **Partial (4 — outcome + ECU=0).** Mexico 2-0; we said 1-0. Correct winner + X-0 read; just under-estimated Mexico's margin. No lesson beyond "the X-0 was right, the margin was thicker than 1." |
