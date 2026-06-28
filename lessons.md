# lessons.md — Prediction Model for the KNOCKOUTS (Round 2+)

_Active calibration for the **knockout rounds** (Round of 32 onward). Round 1's full ledger + retrospective is archived in **`round1_lessons.md`** — read it once for context. The scoring is the **same as the group stage**; what changes is the game dynamics: **every match is win-or-out, both teams trying** (no dead rubbers / content-favorites / rotation)._

**Last updated:** 2026-06-28 — group stage finished **188/426, 2nd of 16** (Ricardo 198, gap 7). Knockouts begin.

---

## 🎯 KNOCKOUT SCORING — same 6/4/3/1/0 (confirmed on the Pollaya `/puntos` page + by Alok)
**The point system is identical to the group stage** — Winner selection +3, each team's goal-count +1, exact +1 bonus, which sum to the familiar tiers:
- **6** = exact scoreline · **4** = correct outcome + one team's goal count · **3** = correct outcome only · **1** = wrong outcome + one team's goal count · **0** = nothing.
- Tournament-long bonuses (set pre-tournament): **champion +10, runner-up +10.**

**The ONLY knockout difference — penalties:** a match is scored on its **90/120-minute result**. **Penalties are excluded** → a tie that's level after extra time is scored as a **DRAW**, and predicting the shootout winner earns **nothing**. So predict the result *within* 90/120 minutes.
- _Check (actual 1-1, won on pens): predict 1-1 → 6; 0-0/2-2 → 3; 1-0/2-1 → 1; 2-0 → 0. (3 is impossible vs a draw.)_

---

## ⭐ NORTH STAR (same model as the group stage — it's the same scoring)
1. **Outcome first, then scoreline.** Correct W/D/L is a guaranteed 3 and the gateway to 4/6; wrong outcome caps at 1. Fix the outcome, then optimize the score.
2. **Back the bookmaker favorite** to win unless a concrete, verified reason says otherwise.
3. **Predict the single most-likely (modal) scoreline.** Concentrate on **common scores (1-0, 2-1, 1-1, 2-0, 0-1)**; **never 0-0 → use 1-1**.
4. **X-0 floor** for a clear favorite likely to keep a clean sheet (the 4-pt floor rule).
5. **For two even, organized sides → predict the 1-1 draw.** A knockout tie counts as a *draw* (penalties excluded), so 1-1 is a real, scoring pick — **never predict the penalty winner.** Jun 28 proved we can call draws (ALG-AUT 3-3, COL-POR 0-0 both hit).
6. **Don't over-inflate margins.** Knockouts are cagier/lower-scoring than group blowouts; the modal favorite win is usually **1-0 / 2-1 / 2-0**, not 3-1. Back a big margin only in a genuine mismatch.

## Knockout regime notes (what's different — it's the game, not the scoring)
- **No dead rubbers / content favorites / rotation** — every game win-or-out, both trying. R1's biggest leak (favorites coasting in low-stakes games, the v2.12 motivation-mismatch) is **gone** — don't apply those overrides here.
- **Cagier, lower-scoring** → favor 1-0 / 2-1 / 1-1; fewer blowouts.
- **Genuine mismatch** (group winner vs a 3rd-place qualifier) → back the favorite with a clean decisive score (often X-0). **Two evenly-matched sides** → 1-1 is live (and a tie is scored as a draw).

## Operational (hard rule)
- **Validate every load-bearing claim** (form, injuries, a cited result) *including its context* before locking a score (see workflow Phase 4).
- **After generating picks: list them for Alok, enter on the app, and RELOAD-VERIFY each is saved.** R1 lost ~5 pts to two un-submitted picks. The app is the source of truth for schedule + scoring.

---

## Lesson log — Knockouts (per-match takeaways)
| Date | Match | What we learned |
| :--- | :--- | :--- |
| _(filled as the Round of 32 is graded)_ | | |
