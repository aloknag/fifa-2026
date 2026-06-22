# lessons.md — Prediction Algorithm Calibration

_The evolving model behind the predictions in `Alok_FIFA_2026_Predictions.md`. Read both files together. Each daily scan reviews graded results and updates this file when a systematic error appears (bump a version, explain the adjustment)._

**Last updated:** 2026-06-22 — graded Jun 21 slate (**+8 pts**: ESP-SAU 4, NZL-EGY 4, BEL-IRN 0, URU-CPV 0 → **94/234** from 39 graded). The X-0/X-1 floor logic is now solid (both correct-outcome picks banked the 4pt floor; v2.9 test worked both ways). The leak moved to the **outcome**: both misses were favorites we backed to WIN that drew (BEL 0-0 IRN, URU 2-2 CPV). Added **v2.10** (Wounded-Favorite / Serial-Drawer draw profile).

---

## ⭐ NORTH STAR — OUTCOME ACCURACY FIRST (read this before anything else)

Getting the **result (W/D/L) right** is the whole game. Correct outcome = a **guaranteed 3 pts** floor and the only gateway to 4 and 6. Wrong outcome = a **ceiling of 1 pt** (usually 0). So flipping one outcome wrong→right is worth ≈ **+3 pts**; refining a scoreline is worth ≈ **+0.5–1**. Always fix the outcome first, then optimize the scoreline.

**Our own data shows where we bleed (through 39 games, outcome accuracy 20/39 = 51%):**
- **Draw picks: 2/8 correct (25%)** — only BEL-EGY & NED-JPN hit; KOR-CZE, CIV-ECU, FRA-SEN, ENG-CRO, GHA-PAN, MEX-KOR all missed.
- **Win picks: 18/31 correct (58%)** — MD2 win picks converting steadily; the misses cluster on one profile: wounded/wasteful favorites that get held to a draw (BEL, URU; see v2.10).

Draws have only a ~27% base rate and are the hardest outcome to call. **Over-predicting draws was our original error; the mirror error has now appeared — backing wounded favorites to win when the draw was live (v2.10). Both are outcome errors; neither is fixed by tweaking the scoreline.**

### The standing rules (apply in order)
1. **Default = back the bookmaker favorite to WIN.** The moneyline is the best outcome predictor available. If a side is −150 or shorter, back it to win unless there's a concrete, verified reason not to (key absence, must-win desperation flipping the script, etc.).
2. **Predict a DRAW only when the draw is the single most likely outcome** — i.e. a true pick-'em (both sides within a narrow band) between two organized defenses with a low total. This is rare. When torn between a narrow-favorite win and a draw, **take the win.**
3. **Don't back underdogs or chase upsets** without a specific, verified edge. One-off upsets (AUS over TUR, CPV holding ESP) are variance, not a pattern to bet.
4. **Then, and only then, pick the scoreline** using the Score-Maximizing rules below (never 0-0; X-0 floor for favorites likely to keep a clean sheet; common scorelines for exact hits; lift margins for clear/host blowouts per v2.7).

### Discipline note (stop the whipsaw)
We added a new model version after almost every match (v2.2→v2.7 in a week), each chasing the last result. That over-fitting to 1–4 game samples is itself a source of error. **This North Star is the stable layer.** Treat the versioned ledger below as history/nuance, not as competing instructions — revise the North Star only on a sustained pattern across many games, not a single slate.

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

### v2.6 — Matchday-2 Regime Shift: MD1 Draw Gravity Was Opener-Specific (June 18)
Grading the Jun 17 slate produced the cleanest disconfirmation yet: **every one of the four MD1 predictions missed the outcome, and the two competing models gave opposite errors on the same day.** We backed the elite-attacking-fav WIN (POR 2-0, per v2.5) → actual **1-1 draw** (Portugal held by an organized DR Congo). We backed the DRAW twice (ENG 1-1, GHA 1-1, per v2.4) → ENG **won 4-2** (a -138 fav blew out elite Croatia) and GHA **won 1-0** on a 90+5' winner. Only the straight fav-win read (UZB-COL) scored, and only 3pts (X-0 floor missed — the debutant scored). The lesson is not "tweak the MD1 rule again" — it's that **the entire MD1 draw-gravity corpus (v2.2 / v2.4 / v2.5) describes an opening-match regime** (rust, extreme caution, first-game variance, modal draw). The calendar has now rolled to **Matchday 2**, where teams have shed rust and the better side converts far more reliably. New rules:
- **MD2+ regime: drop the broad draw default.** From Matchday 2 onward, back the stronger/fitter side to WIN when the line and form support it. Do not import "openers gravitate to draws" into MD2 — it is not the same population.
- **Reserve the draw lean for genuinely even MD2 matchups** (true pick-'em lines, e.g. MEX-KOR +105, SCO-MAR −135 with a fit organized underdog), not for any competitive game.
- **Don't auto-assume the X-0 zero against organized debutants (extends Rule 2).** UZB-COL: Colombia won but Uzbekistan scored (Fayzullaev) — a competent debutant that gets numbers forward will often get on the board. Reserve X-0 for genuinely leaky opponents or dominant clean-sheet favorites; otherwise X-1 protects the 3pt floor without betting the opponent blanks.
- **Late-winner pattern persists across matchdays:** GHA-PAN was 0-0 into the 90th then 1-0 (the CIV-ECU shape). Floor games still break 1-0, not 0-0 — keep Rule 1 (never 0-0).
- **Caveat — small MD2 sample.** v2.6 is a regime call made on a single rolled-over calendar, not yet on graded MD2 results. Grade the Jun 18-20 slate hard; if MD2 favorites also stumble, the issue is our favorite-strength read, not the matchday regime.
- **Process: verify fixture dates against the source's local calendar.** The re-prediction pass found MEX-KOR logged on Jun 18 when ESPN's ET calendar has it Jun 19 (1 AM ET), and BRA-HAI/TUR-PAR logged Jun 19 when they're Jun 20 (early-AM ET). Late-night-ET kickoffs of games "felt" as the prior evening drift one day off. Always slot a fixture by the **ET date ESPN files it under**, not by intuition. _(Jun 19 correction: BRA-HAI is actually Jun 19, 9 PM ET in Philadelphia — Eastern venue, not the post-midnight Jun 20 it was filed as. Only the Pacific TUR-PAR is genuinely Jun 20, 12 AM ET.)_

### v2.7 — Host-Adrenaline Blowouts & Persistent Margin Timidity (June 19)
Grading the first real Matchday-2 slate **validated v2.6's core call but exposed the next leak.** Favorites converted (SUI won, CAN won, MEX won; only depleted-but-stubborn Czechia escaped with a 1-1), and our lone draw-lean (MEX-KOR +105 → MEX 1-0) was the miss — confirming "drop the broad draw default in MD2." But three of four were "right side, **margin far too low**": **SUI 2-1 → 4-1**, **CAN 2-1 → 6-0**, echoing GER/SWE/NOR. The hosts in particular are routing weak sides. New rules:
- **Host-adrenaline now means blowout, not just a win.** Co-hosts at home are producing lopsided scores: USA 4-1, CAN 6-0, plus MEX winning. For a host vs a weak/depleted/leaky opponent, project **3+ goals** and **take the X-0** — Canada 6-0 would have hit the 4pt floor on a 2-0, but we abandoned the zero (softened to 2-1) and lost a point. Don't fear an organized opponent's MD1 goal so much that you surrender the host clean sheet vs a side that just got blown out itself (Qatar had scored on MD1, then shipped six).
- **Margin timidity is the dominant leak (extends v2.3/v2.5).** When you have the right favorite, push the goal count: strong/host favorites vs weak or depleted sides are landing on 4–6, not 2. Our default winning margin should rise from "2-1" to "3-1 / 3-0" for clear talent gaps.
- **A depleted underdog is not an automatic blank/loss.** South Africa, down to a thinned squad and beaten on MD1, still drew Czechia 1-1 via a late penalty. A modest favorite (-125) is not a lock; keep the X-1 / draw-aware floor when the "favorite" edge is small and the underdog can win a set-piece or penalty.
- **Reaffirm the genuine-pickem draw (v2.6):** reserve 1-1 for two-organized-defense coin-flips (SCO-MAR −135). MEX-KOR taught the limit — a *host* at a near-pickem line should be leaned toward the win, not the draw.

### v2.8 — X-0 Commitment & Coin-Flip Caution (June 20)
Grading the Jun 19–20 slate produced the **best single-slate score yet (+17, two exacts)** and validated the outcome-first North Star (3/4 correct outcomes, 75%). But the one points leak — USA 2-1 → actual 2-0 (4pts instead of the 6pt exact) — repeats the same error as CAN (softened from 2-0 to 2-1, missed the 4pt floor). Hosts keep blanking opponents and we keep fearing the opponent's goal. New rules:
- **Commit fully to X-0 for host favorites.** USA 2-0, CAN 6-0, MEX 1-0 — all three co-hosts won with clean sheets in their home games. When predicting a host win vs a weak/depleted side, lock in the zero. We have now lost points on X-0 softening **twice** (CAN 2-1→6-0, USA 2-1→2-0). The organized-opponent fear is costing more than the occasional opponent goal would.
- **True coin-flips (lines ±110) with mutual desperation are genuinely 50/50 — lower confidence, so play for the consolation floor with X-1, NOT X-0.** TUR -105 vs PAR was the slate's only miss. Both teams were desperate (TUR lost MD1, PAR lost 1-4) and the line was essentially even. An early Galarza stunner (2') and a smash-and-grab held despite Almirón's red card. The X-0 floor (Rule 2) only protects you when you are *confident in the winner* — in a coin-flip you might back the wrong side, and then an X-0 scores **0** while an X-1 still banks **1pt** when the opponent scores the modal 1. Proof: we predicted TUR 2-1 → got 1pt (PAR's 1 matched); a "tidy" 2-0 would have scored 0. So when the line says "coin flip" and both teams are all-in, **don't pretend you can pick the winner — predict X-1 (e.g. 2-1), keeping the loser-scores-1 consolation, and accept these are low-confidence plays whose realistic floor is 1pt, not 3.**
- **Outcome-first North Star is the dominant driver.** SCO-MAR (flipped from draw to Morocco win → exact 🎯) was the signature call. BRA-HAI 3-0 exact proves v2.3/v2.7 margin-lift is calibrated for elite-vs-weak. Keep the discipline: back the favorite, lift the margin, take the zero.

### v2.9 — X-0 Commitment Generalized & the "Toothless-vs-Threatening" Test (June 21)
Grading Jun 20 (+14, GER-CIV exact) showed the X-0-vs-X-1 *judgment* is now the deciding skill — and on the three **X-1 withhold** calls (GER, NED, TUN) we split 2/3. The two correct withholds (GER, NED) and one wrong withhold (TUN softening) point to a single, cleaner rule than v2.8's host-only framing:
- **Generalize the X-0 commitment from "hosts" to ANY clear favorite (≈ -180 or shorter) vs a toothless/weak attack.** TUN-JPN: Japan -187 thrashed a desperate, must-win Tunisia **0-4** (TUN-JPN order); we softened to 1-2 fearing they'd "commit forward," but a desperate underdog committing forward gets **picked off on the counter and blanked** — desperation ≠ they will score. The X-0 (0-2) was the 4pt floor; we banked 3. This is the same softening leak as CAN and USA. Stop fearing the weak side's goal when the favorite is clearly superior.
- **The boundary — the "toothless-vs-threatening" test (withhold the X-0 only when BOTH: the opponent has a genuine, demonstrated attacking threat AND the favorite itself leaks).** GER-CIV is the model: Germany has no WC clean sheet in 7 (leaks) and CIV was organized + on a win streak + a real attack → we correctly took X-1 and nailed the 2-1 exact. NED-SWE likewise: Sweden attacks well, so X-1 → Sweden scored → 4pt. So: *toothless opponent → X-0; threatening opponent + leaky favorite → X-1.* Apply this test explicitly per fixture instead of a blanket rule.
- **Reaffirm v2.4 (organized-debutant exception) — and DON'T over-lift the margin against bus-parkers.** ECU 0-0 CUW repeated ESP 0-0 CPV exactly: a bunkering debutant + hot keeper (Eloy Room, 15 saves) held a **-909** favorite scoreless — even though Curaçao had shipped 7 to Germany. A team that gets blown out by an elite attack can still bunker-and-hold a *modest* favorite. So vs a CPV/CUW-type low-block, back the favorite but keep the margin **tight (1-0)** and accept genuine draw variance — over-committing to a 2-0/3-0 here is the ECU-CUW error. _(Directly informs the URU-CPV pick: 1-0, not 2-0.)_
- **Two axes — don't conflate them (the ECU-CUW correction).** The toothless-vs-threatening test sets the *scoreline* (X-0 vs X-1: will the opponent score?), driven by their **attack**. It does NOT set the *outcome* (will the favorite win?), driven by the opponent's **defense**. TUN and CUW were both toothless-attack → the rule calls for X-0 on both (we took it on ECU-CUW, but wrongly softened TUN to 1-2); TUN was open/desperate (routed 0-4 → the X-0 *would have* banked the 4pt floor we missed) while CUW bunkered behind a hot keeper (held 0-0 → the X-0 we took banked only the 1pt consolation). So the X-0 "4pt floor" is **conditional on the win** — against a proven low-block it can collapse to 1pt. Take the X-0, but rate the *outcome* as coin-flip-ish, not a lock, when the opponent is a bunker debutant. _(URU-CPV: the 1-0 scoreline is right; the win itself is closer to ~60/40 than the -200 line implies.)_
- **Margin timidity remains the secondary leak (v2.3/v2.7).** NED 2-1 → 5-1: elite favorites keep routing. When the favorite is elite AND the opponent is not a bus-parker, lift the winning margin to 3+.

### v2.10 — The Wounded-Favorite / Serial-Drawer Draw Profile (June 22)
Grading Jun 21 confirmed the scoreline floor is solved (both correct-outcome picks banked 4pts) and isolated the remaining leak as the **outcome**: both misses (BEL 0-0 IRN, URU 2-2 CPV) were favorites we backed to WIN that instead drew. v2.9 correctly warned the win is *not lockable* vs a bunker (it rated URU-CPV ~60/40) — but we still logged the win and took 0. The fix is to actually act on that downgrade. There is a recognizable profile where the draw is the live, often modal, outcome even for a market favorite:
- **The Wounded Favorite.** A favorite missing a key attacker, or hit by an early red card, vs an organized opponent with a hot keeper. Belgium: Doku out, Ngoy red (66'), Beiranvand 7 saves → 0-0 despite 23 shots. The line (-230) was stale to the absence; the goal threat was gutted. **When a favorite's attack is materially reduced (absence/red card) and the opponent is organized + keeper-strong, the draw is the single most likely outcome — predict 1-1, don't back the win.**
- **The Serial Drawer.** An organized underdog that has *already held a strong team* is a proven draw machine, not a one-off — and is being systematically over-priced against. Cape Verde held Spain 0-0, then drew Uruguay 2-2 (and **scored twice** — so they are not even "toothless"; the X-0 read was doubly wrong). **Once a side has held one favorite, downgrade the next favorite they face toward a draw, and do NOT assume the X-0 against them.**
- **The chronically-wasteful favorite.** Uruguay drew SAU 1-1 then CPV 2-2 — a "favorite" that doesn't finish is a draw risk every game. Weight recent conversion, not just the moneyline.
- **Discipline guard (don't re-trigger the old error).** This is NOT a return to broad draw-leaning (draw picks remain 2/8 = 25%; CIV/FRA/ENG/GHA/MEX punished that). It is a *narrow, profile-gated* draw call: predict the draw ONLY when a concrete wound (key absence / red card / proven serial-holder / misfiring fav) is present. Absent that, keep backing the favorite to win (North Star Rule 1). The EV math: a 1-1 call on a true draw banks 3pts vs the 0 a backed-win takes; but a 1-1 on a game the favorite wins also risks 0–1pt, so only spend it when the wound is real.
- **Objective market-gate (red-team refinement, Jun 22).** The narrative "wound" triggers above are subjective and risk hindsight bias. Add a hard, checkable gate: **only consider the draw when the bookmaker's no-vig draw probability is at or above the favorite's win prob — i.e., the draw is the single most likely outcome (per North Star Rule 2).** If the favorite is a clear modal outcome (e.g. NOR-SEN: NOR 45% vs draw 27%), DO NOT predict the draw no matter how "open" the game feels — back the favorite. The market is a better outcome predictor than our narrative. The wound triggers refine *within* games the market already prices as draw-live; they do not override a clear favorite.
- **Variance caveat — don't over-fit to BEL.** Belgium's 0-0 was driven by a 66' red card, which is variance, not a repeatable signal. The durable lessons from this slate are the *Serial Drawer* (Cape Verde — a pattern across two games) and the *market-gate* (objective). Weight those; treat the red-card case as a one-off, not a reason to fear every elite favorite.
- **Floor logic reaffirmed (v2.9 holds).** When you DO back the favorite to win: X-0 vs a leaky/open opponent that comes out to play (ESP 4-0 SAU ✓), X-1 vs an opponent with a demonstrated goal (NZL scored ✓). Both paid the 4pt floor this slate.

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
- **Historical proof:** ARG 1-0 → actual 3-0 earned **4pts** (ARG won ✓ + Algeria's 0=0 ✓ — the away-0 was a free second match). Counter-case: GER-CUW (predicted 4-0, got 7-1) — the 0 didn't land because Curaçao scored. So only take the 0 when the loser *genuinely* looks like a zero-scorer (disciplined/limited attack), not in an open, leaky game.

### Rule 3 — Exact-score hunting: concentrate on common scorelines
- 1-0, 1-1, 2-0, 2-1 account for the majority of WC match results. Predicting exotic scores (4-2, 3-3) chases the 6pt jackpot on very low-probability outcomes.
- When two scorelines feel equally likely, pick the one that also maximizes partial credit if wrong (see Rule 2).

### Rule 4 — Expected-value ordering for uncertain matches
When outcome confidence is low, rank predictions by their worst-case floor, not their upside:
1. X-0 favorite win → floor is 3pts if winner is right (4pts if loser really scores 0)
2. X-1 favorite win → floor is 3pts if winner is right, 1pt if only loser's goals match
3. 1-1 draw → floor is 0pts if actual is a multi-goal lopsided win; 1pt if one team scores 1
4. 0-0 draw → nearly identical floor to 1-1 but with worse 6pt hit rate — never preferred

### Current score baseline (as of 2026-06-22)
- **94 pts from 39 graded matches** (40.2% efficiency vs 234pt max)
- Exact hits (6pts each): **5 matches** (30/94 = 32% of total score) — HAI-SCT, BEL-EGY, SCO-MAR, BRA-HAI, GER-CIV
- Correct-outcome rate: **20/39 (51%)** — win picks 18/31 (58%), draw picks 2/8 (25%)
- Average per match: **2.41 pts** (down from 2.46 — two zeros this slate); target ≥ 3.0 pts/match
- Losses to 0: now **8** (CAN-BIH, QAT-SUI, AUS-TUR, IRN-NZL, POR-COD, ENG-CRO, **BEL-IRN, URU-CPV**) — the two new ones are both the Wounded-Favorite/Serial-Drawer profile (v2.10)
- **Jun 21 was a modest slate: +8 from 4 matches (2.0 pts/match), no exact.** The floor logic was perfect — both correct outcomes hit the 4pt floor (ESP X-0 → SAU 0=0; NZL X-1 → NZL scored). Both zeros were favorites that drew (BEL, URU); calling either a draw banks 3pts → v2.10. **Standing: app shows Alok 5th at 95, leader 104 (gap 9, widened from 7). Floors keep pace; only exacts close the gap.**

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
| Jun 17 | POR vs COD | 2-0 → 1-1. Elite-attacking-fav-win (v2.5) failed on MD1 — Portugal held by an organized debutant. The MD1 model is unreliable in both directions. (→ v2.6) |
| Jun 17 | ENG vs CRO | 1-1 → 4-2. A modest fav (-138) blew out elite Croatia; MD1 draw lean badly wrong. Opposite error to POR same day. (→ v2.6) |
| Jun 17 | GHA vs PAN | 1-1 → 1-0. 0-0 into the 90th, Yirenkyi won it 90+5'. Late-winner/floor pattern persists; GHA 1=1 saved 1pt. (→ v2.6) |
| Jun 17 | UZB vs COL | 2-0 → 1-3. Fav win ✓ (3pts) but the debutant scored — don't auto-assume the X-0 zero vs an organized side. (→ v2.6) |
| Jun 18 | CZE vs RSA | 1-0 → 1-1. A modest MD2 fav (-125) failed to beat a depleted RSA; late pen. Small favorite edges aren't locks — CZE 1=1 saved 1pt. (→ v2.7) |
| Jun 18 | SUI vs BIH | 2-1 → 4-1. v2.6 fav-converts ✓ and BIH 1=1 → 4pts, but margin under-shot (5 goals in 23'). Lift winning margins. (→ v2.7) |
| Jun 18 | CAN vs QAT | 2-1 → 6-0. Host blowout (J. David hat-trick). We softened off the X-0 and lost the 4pt floor; host adrenaline = rout, take the zero vs a weak side. (→ v2.7) |
| Jun 19 | MEX vs KOR | 1-1 → 1-0. Host won a near-pickem; don't auto-draw a host even at +105. MEX 1=1 saved 1pt. (→ v2.7) |
| Jun 19 | USA vs AUS | 2-1 → 2-0. 🎯 Outcome ✓ (4pts, USA 2=2). But X-0 (2-0) would have been the **exact** — softened to 2-1 and lost 2pts. Third time hosts blanked (CAN 6-0, MEX 1-0, now USA 2-0). Stop fearing the opponent goal for hosts. (→ v2.8) |
| Jun 19 | SCO vs MAR | 0-1 → 0-1. 🎯 **EXACT HIT.** The outcome-first flip (1-1 draw → 0-1 Morocco win) was the best single call of the tournament. Saibari struck after 72 seconds. Back the favorite, not the draw. (→ North Star validated) |
| Jun 19 | BRA vs HAI | 3-0 → 3-0. 🎯 **EXACT HIT.** v2.3 blowout ceiling + v2.7 margin lift + X-0 floor all converged perfectly. Cunha + Vinícius ×2. Elite attack vs beatable minnow with a real margin and a blank — model fully calibrated for this profile. |
| Jun 20 | TUR vs PAR | 2-1 → 0-1. Miss. Galarza long-range stunner (2') for Paraguay; Almirón red (45') but they held despite 33 TUR shots. A -105 coin-flip with mutual desperation is genuinely unpredictable. (→ v2.8) |
| Jun 20 | GER vs CIV | 2-1 → 2-1. 🎯 **EXACT HIT.** Undav brace off the bench (68', 90+4') after Kessié's opener. The deliberate X-1 withhold (Germany leaks → CIV scores) was exactly right — the "threatening opponent" half of the test. (→ v2.9) |
| Jun 20 | ECU vs CUW | 2-0 → 0-0. Miss. A bunkering debutant + hot keeper (Eloy Room, 15 saves) held a -909 favorite scoreless — the ESP-CPV 0-0 pattern again. Don't over-lift the margin vs a low-block; CUW 0=0 saved 1pt. (→ v2.9 reaffirms v2.4) |
| Jun 20 | NED vs SWE | 2-1 → 5-1. Win (4pts, SWE 1=1). X-1 withhold paid off (Sweden scored) but margin badly under-shot — elite favorites keep routing. Margin timidity persists. (→ v2.9/v2.7) |
| Jun 20 | TUN vs JPN | 1-2 → 0-4. Win (3pts). Softened to X-1 fearing a must-win Tunisia would commit forward; they got picked off and **blanked** — the X-0 (0-2) was the 4pt floor. Clear fav vs toothless side → take the zero. (→ v2.9) |
| Jun 21 | ESP vs SAU | 3-0 → 4-0. Win (4pts, SAU 0=0). X-0 paid off — restored elite attack vs a side that came out to play (not a bunker) → clean-sheet rout. v2.9 validated. Margin under by one. |
| Jun 21 | BEL vs IRN | 2-1 → 0-0. Miss (0pts). Wounded favorite: Doku out + Ngoy red (66') + Beiranvand 7 saves → held despite 23 shots. A 1-1 call banks 3pts. Don't back a gutted attack to win vs an organized keeper-strong side. (→ v2.10) |
| Jun 21 | URU vs CPV | 1-0 → 2-2. Miss (0pts). Cape Verde's 2nd straight draw (held ESP, drew URU) and they SCORED twice — a proven serial-drawer, not toothless. Wasteful Uruguay won't convert. Downgrade the next fav vs a proven holder. (→ v2.10) |
| Jun 21 | NZL vs EGY | 1-2 → 1-3. Win (4pts, NZL 1=1). X-1 withhold paid off — NZL's real attack (2 vs Iran) scored, exactly as the v2.9 threatening test called. Egypt's class told. Margin under by one. |

---

## How to evolve this file
1. After grading each match, add a one-line takeaway to the lesson log.
2. If the same error repeats across matches, create the next version (v2.2, v2.3, …) describing the rule change and why.
3. Keep the "Active calibration model" section as the current source of truth the predictions apply.
