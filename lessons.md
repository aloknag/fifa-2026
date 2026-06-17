# lessons.md — Prediction Algorithm Calibration

_The evolving model behind the predictions in `Alok_FIFA_2026_Predictions.md`. Read both files together. Each daily scan reviews graded results and updates this file when a systematic error appears (bump a version, explain the adjustment)._

**Last updated:** 2026-06-17

---

## Active calibration model

### v1.0 — Baseline (Structural-Defensive Weighting)
Assumed rigid Matchday-1 anxiety, heavy "Under 2.5".
**Flaw:** underestimated home-soil psychology and early-game chaos.

### v2.0 — Event-Driven Momentum Engine
- **Host-Nation Adrenaline Adjuster (+1.5 xG):** co-hosts in packed domestic venues bypass opening-day sluggishness — shift from 1-0s to multi-goal margins.
- **The Chaos Pivot (first 25 min):** an early goal/red card shattering an underdog's bunker → pivot the live model to "Over 3.5".
- **Roster Verification Check:** track star engine players; if a key player is absent, subtract 0.5 xG from that team.

### v2.1 — Neutral-Venue Margin Discipline & Defensive Floor (June 13)
- **Host modifier is HOST-ONLY.** Do not apply attacking aggression to neutral-venue games between non-host nations. The original 0-3 (SUI) and 0-2 (SCT) over-applied this to games the market expects tight. Default favorite-vs-deep-block openers to 1-0 / 2-0, not 3-goal margins.
- **Group-label verification:** cross-check every fixture's group against an official source before logging. (Caught HAI–SCT mislabeled "Group I"; correct = Group C.)
- **Defensive-floor flag:** when BOTH teams rank elite defensively (e.g., CIV/ECU), bias toward Under and the draw, not a multi-goal favorite.
- **Roster check confirmed valuable:** Neymar's calf and Japan's Mitoma/Minamino/Endo absences both lower attacking xG — keep −0.5 xG per absent key engine.

### v2.2 — Matchday-1 Favorite Drag (June 14)
Grading the Jun 13 + AUS-TUR slate exposed a clear systematic error: **neutral-venue Matchday-1 favorites keep failing to win.** We backed SUI (-350) → 1-1 draw, BRA (-170, Neymar out) → 1-1 draw, and TUR → lost 0-2 to Australia. Opening matches carry rust, caution, and high upset variance. New rules:
- **Default tight neutral-venue MD1 games to a DRAW**, not a narrow favorite win, when EITHER the favorite is weakened (key player out) OR the opponent is a solid/elite side. (Would have flipped BRA-MAR and QAT-SUI toward the actual draws.)
- **Reserve the narrow 1-0 favorite win for clear talent mismatches vs genuinely weak opponents** — exactly the HAI-SCT 0-1 we nailed. This is the one profile where favorites are converting.
- **Respect organized underdogs.** Don't auto-back the nominal favorite; a disciplined, fully-fit underdog (Australia) can win to nil, especially if the favorite rotates (Türkiye rested Yıldız).
- This *extends* v2.1 margin discipline: v2.1 shrank the margin; v2.2 says for the toss-up tier, take the draw outright.

### v2.3 — Blowout Ceiling & Qualifying-Defense Discount (June 15)
Grading the full Jun 14 slate flipped the dominant error: in clear mismatches our **outcome** calls are now right, but the **margins are far too timid.** GER (predicted 4-0 → actual 7-1) and SWE (predicted 1-0 → actual 5-1) were both correct-side wins that badly under-shot the goal count. New rules:
- **Blowout ceiling for elite/strong attacking favorites vs weak or debutant defenses:** don't cap these at 1-0/2-0 — project **3–5 goal margins**. The HAI-SCT 1-0 profile is for *defensively organized* minnows; an open, leaky minnow (Curaçao) or an out-classed mid-tier side that commits forward (Tunisia) gets buried.
- **Discount an underdog's qualifying defensive record when it was earned vs weak confederation opposition.** Tunisia's "22-0 GD, zero conceded" qualifying line collapsed (5-1) against a real attack — it was padded by weak CAF fixtures. Weight the *strength of schedule* behind any clean-sheet stat.
- **Defensive-floor games still break 1-0, not 0-0.** CIV-ECU was 0-0 deep into the 90th, then Amad Diallo won it (90'). When two elite defenses meet, lean to a **1-0 edge** for the side with more late-game quality / the slight market fav, rather than a flat 0-0.
- **v2.2 draw lean confirmed:** NED-JPN landed as the predicted draw (2-2) — keep defaulting weakened-favorite-vs-strong-opponent MD1 games to a draw.

### v2.4 — Matchday-1 Draw Gravity & Organized-Debutant Exception (June 16)
Grading the full Jun 15 slate gave the starkest signal yet: **all four openers were draws and every favorite failed to win** — ESP 0-0 CPV (a ~-1000 fav held scoreless), BEL 1-1 EGY (predicted ✓), SAU 1-1 URU (a fully-fit -220 fav), IRN 2-2 NZL. This broadens v2.2 well past "weakened favorite or elite opponent":
- **MD1 draw gravity is broad and strong.** The modal opening-match result is a draw, and even big, fully-fit favorites routinely fail to win. Default ALL competitive MD1 games to a draw unless it's a true elite-vs-weak-AND-leaky mismatch.
- **Organized-debutant exception to the v2.3 blowout ceiling.** v2.3's "elite attack vs weak/debutant defense = 3–5 goals" applies only to *leaky/open* minnows (Curaçao 7-1). A *disciplined low-block* debutant with a hot keeper (Cape Verde + Vozinha, who survived Spain's 27 shots) can hold an elite side to 0-0. Distinguish "leaky minnow → buried" from "organized low-block → frustrates to a draw/1-0."
- **Retire the "class-above fully-fit favorite → narrow win" MD1 exception.** It failed on URU (-220 → 1-1). On MD1, reserve narrow favorite wins for clear mismatches vs genuinely weak sides that also commit forward.

### v2.5 — Elite-Attacking-Favorite Exception to MD1 Draw Gravity (June 17)
Grading Jun 16 sharply **reversed** the Jun 15 draw wave: all three favorites WON — **FRA 3-1 SEN** (beating an *elite* opponent), **NOR 4-1 IRQ**, **ARG 3-0 ALG** — two by 3+ goals. The common thread: each winner was a genuinely **elite attacking side, fully fit, with an in-form superstar** (Mbappé, Haaland, Messi). v2.4's broad "default ALL competitive MD1 games to a draw" was too wide and directly cost us FRA-SEN (we logged 1-1; France won 3-1, only 1pt). Refinements:
- **Elite-attacking-favorite exception:** when the favorite is a top-tier attacking side that is fully fit and carries an in-form star, back a **favorite WIN with a real margin (2–3 goals)** — even against a strong/elite opponent (Senegal). Do NOT default these to a draw.
- **Keep the broad draw default ONLY for modest or weakened favorites and genuinely even matchups** (England -138 vs elite Croatia; Ghana -110 minus Partey). The draw gravity is real for the toss-up tier; it is not for elite attackers.
- **Don't over-cap elite-favorite margins (extends v2.3):** Iraq and Algeria are organized, non-leaky sides, yet shipped 4 and 3 — an elite attack buries even a competent underdog. Our 0-2 (NOR) and 1-0 (ARG) caps were too timid; both still scored (3pt + 4pt) but missed the exact.
- **X-0 floor rule validated:** ARG 1-0 → actual 3-0 earned **4pts** because Algeria's 0 matched. Keep predicting X-0 for clear favorites whose opponent plausibly blanks.

---

## Score-Maximizing Strategy

The pool scoring system (6 / 4 / 3 / 1 / 0) creates specific incentives that should shape every prediction, independent of the calibration model. Apply these after determining the likely outcome.

### The tiers and what drives them

| Pts | Condition | How to target it |
| ---: | :--- | :--- |
| **6** | Exact scoreline | Predict the single most probable scoreline; common scores (1-0, 1-1, 2-0, 2-1) hit more often |
| **4** | Correct outcome + one team's goals match | Predict X-0 for favorites — the loser's 0 acts as a free second match |
| **3** | Correct outcome only | Floor when you get the winner but both goal counts miss |
| **1** | Wrong outcome but one team's goals match | Consolation; don't aim for this |
| **0** | Nothing matches | Avoid at all costs |

### Rule 1 — Never predict 0-0; always predict 1-1 for defensive draws
- 0-0 is the rarest draw scoreline and offers no "partial" safety net: if the actual result is 1-0, a 0-0 prediction earns only 1pt (the losing team's 0 matches), same as a 1-1 prediction would.
- 1-1 is strictly better: it hits the exact 6pt mark far more often AND produces the same 1pt consolation when one team scores 1.
- **Historical proof:** CIV vs ECU — predicted 0-0, got 1pt (ECU 0=0 ✓). Predicting 1-0 CIV would have been the 6pt exact.

### Rule 2 — Prefer X-0 over X-1 for clear favorites ("4pt floor rule")
- If the favorite wins but the margin differs, a clean-sheet prediction (X-0) earns **4pts** (winner ✓ + loser's 0=0 ✓), while X-1 earns only **3pts** (winner ✓, goal mismatch on both sides).
- When a loser scoring 0 is plausible (dominant favorite, disciplined defense), always lock in the 0.
- **Historical proof:** GER 4-0 prediction, actual 7-1 → 3pts. If we'd predicted 7-0 or any Y-0, we'd have earned 4pts because GER won and CUW scored 1 (the loser 0=0 check failed here — CUW did score). The lesson: predict X-0 when the loser *genuinely* looks like a zero-scorer.

### Rule 3 — Exact-score hunting: concentrate on common scorelines
- 1-0, 1-1, 2-0, 2-1 account for the majority of WC match results. Predicting exotic scores (4-2, 3-3) chases the 6pt jackpot on very low-probability outcomes.
- When two scorelines feel equally likely, pick the one that also maximizes partial credit if wrong (see Rule 2).

### Rule 4 — Expected-value ordering for uncertain matches
When outcome confidence is low, rank predictions by their worst-case floor, not their upside:
1. X-0 favorite win → floor is 3pts if winner is right (4pts if loser really scores 0)
2. X-1 favorite win → floor is 3pts if winner is right, 1pt if only loser's goals match
3. 1-1 draw → floor is 0pts if actual is a multi-goal lopsided win; 1pt if one team scores 1
4. 0-0 draw → nearly identical floor to 1-1 but with worse 6pt hit rate — never preferred

### Current score baseline (as of 2026-06-17)
- 42 pts from 19 graded matches (36.8% efficiency vs 114pt max)
- Exact hits (6pts each) still just 2 matches (12/42); correct-outcome rate 8/19 (42%)
- Average per match: 2.2 pts; target ≥ 3.0 pts/match to outperform field
- Losses to 0: still 4 (CAN, QAT, AUS, IRN) — none on Jun 16; the X-0 floor rule + correct-side calls kept all three Jun 16 picks scoring (1/3/4)
- Margin discipline is now the main leak: 3 of the last 6 graded were "win, wrong margin" (under-shot). v2.5 lifts margins on elite attacking favorites

---

## Lesson log (per-match takeaways)

| Date | Match | What we learned |
| :--- | :--- | :--- |
| Jun 11 | MEX vs RSA | Early breakthroughs + red cards open up "rigid" games — don't cap goals at the clean-sheet ceiling. |
| Jun 11 | CRC vs RCH | Two transition-happy sides play more openly than tactical models assume. |
| Jun 12 | CAN vs BIH | Always confirm star availability pre-kickoff (Davies benched); set-piece frailty breaks clean sheets. |
| Jun 12 | USA vs PRY | Host adrenaline + early own goal can blow past predicted margins → birth of v2.0. |
| Jun 13 | QAT vs SUI | Even a -350 favorite can be held to a draw on MD1; a deep block + late goal beats the "narrow favorite win." Backed SUI win → 1-1. (→ v2.2) |
| Jun 13 | BRA vs MAR | A weakened favorite (Neymar out) vs a strong opponent should be a DRAW, not a 1-0 win. Roster flag right, conclusion wrong → 1-1. (→ v2.2) |
| Jun 13 | HAI vs SCT | 🎯 Exact hit (0-1). The disciplined 1-0 favorite call works ONLY for clear mismatches vs weak sides — keep this profile. Validates v2.1. |
| Jun 14 | AUS vs TUR | Don't auto-back the favorite: an organized underdog won 2-0 after Türkiye rested Yıldız. Respect fit, disciplined underdogs. (→ v2.2) |
| Jun 14 | GER vs CUW | Right side, far too timid (4-0 → 7-1). Elite attack vs leaky debutant = 5+ goals, not a tidy 4-0. (→ v2.3) |
| Jun 14 | NED vs JPN | 🎯 Outcome hit: predicted draw, got 2-2. v2.2's "weakened favorite vs strong opponent → draw" works — keep it. |
| Jun 14 | CIV vs ECU | Defensive-floor read was right (0-0 to the 90th) but a 90' winner made it 1-0. Floor games break 1-0, not 0-0. (→ v2.3) |
| Jun 14 | SWE vs TUN | 1-0 → 5-1. Tunisia's spotless qualifying defense was padded by weak CAF opp.; discount clean-sheet stats by schedule strength. (→ v2.3) |
| Jun 15 | ESP vs CPV | 4-0 → 0-0. An *organized low-block* debutant + hot keeper held a -1000 fav scoreless (27 shots). The blowout ceiling is for *leaky* minnows only. (→ v2.4) |
| Jun 15 | BEL vs EGY | 🎯 Exact (1-1). v2.2 draw lean again — MD1 favorite vs an organized, solid opponent (Egypt/Salah) = draw. |
| Jun 15 | SAU vs URU | 0-1 → 1-1. A fully-fit class-above favorite (URU -220) still couldn't win on MD1. Retire that exception for openers. (→ v2.4) |
| Jun 15 | IRN vs NZL | 1-0 → 2-2. Low-scoring lean wrong; another MD1 favorite held. Opening matches gravitate to draws. (→ v2.4) |
| Jun 16 | FRA vs SEN | 1-1 → 3-1. Don't default an elite, fully-fit attacking favorite to a draw even vs an elite opponent — Mbappé brace, France's class told. (→ v2.5) |
| Jun 16 | IRQ vs NOR | 0-2 → 1-4. Outcome ✓ but margin far too timid; an elite attack (Haaland) buries even an organized underdog — stop over-capping. (→ v2.3/v2.5) |
| Jun 16 | ARG vs ALG | 1-0 → 3-0. 🎯 X-0 floor rule earned 4pts (ALG 0=0). Messi hat-trick; margin too low for the exact — lift elite-favorite goal counts. (→ v2.5) |

---

## How to evolve this file
1. After grading each match, add a one-line takeaway to the lesson log.
2. If the same error repeats across matches, create the next version (v2.2, v2.3, …) describing the rule change and why.
3. Keep the "Active calibration model" section as the current source of truth the predictions apply.
