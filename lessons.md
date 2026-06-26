# lessons.md — Prediction Algorithm Calibration

_The evolving model behind the predictions in `Alok_FIFA_2026_Predictions.md`. Read both files together. Each daily scan reviews graded results and updates this file when a systematic error appears (bump a version, explain the adjustment)._

**Last updated:** 2026-06-26 — graded Jun 25 slate (**+15 pts**: CUW 0-2 CIV 🎯6, ECU 2-1 GER 1, JPN 1-1 SWE 1, TUN 1-3 NED 🎯6, PRY 0-0 AUS 1, TUR 3-2 USA 0 → **155/354** from 59 graded). **NEW VERSION v2.12 — the Stakes-Asymmetry / Unmotivated-Favourite Override.** The exact drought broke (CIV X-0, NED X-1-withhold — both clear-favourite + clear-stakes games), but **only 2/6 outcomes**: the 4 misses were all the motivation-mismatch profile we've now seen ≥3 times — **ECU 2-1 GER** (Germany seed-locked → indifferent → lost to must-win Ecuador; we FLAGGED it and backed the -188 fav anyway) joins **RSA 1-0 KOR** and **AUS 2-0 TUR**. Fix: **when a favourite is unmotivated (qualified + nothing to gain, or rotating) AND the opponent is must-win, the v2.10 market-gate is invalid — predict the draw or the desperate side, don't back the stale-line favourite.** Also: a dead rubber (TUR 3-2 USA) is open chaos, not a quiet 1-1 — Rule 5 is for *motivated* coin-flips. Eliminated-free tail CONFIRMED (TUN 1-3 NED exact). _(Prior: 2026-06-25 — graded Jun 24 +14; logged the two tails that v2.12 now versions.)_

<details><summary>Prior header (v2.11 introduction, 2026-06-24)</summary>

**Last updated:** 2026-06-24 — graded Jun 23 slate (**+11 pts**, no zeros but only 2.75 pts/match: POR 5-0 UZB = 3, COL 1-0 COD = 3, CRO 1-0 PAN = 4, ENG 0-0 GHA = 1 → **126/282** from 47 graded). **NEW VERSION v2.11** — the X-1 withhold misfired a 3rd time (TUN-JPN, now POR-UZB & COL-COD): every time we withheld the clean sheet against a clear/heavy favorite because the weak opponent had a "demonstrated goal," the opponent was BLANKED. COL 1-0 was the exact we listed as our own alt. **Fix: heavy favorite (-200 or shorter, i.e. ≤ -200) → take the X-0 regardless of the opponent's prior goal; reserve the X-1 withhold for moderate (> -200), genuinely-leaky favorites.** The one pick that worked — CRO PAN (predicted 2-0 / actual 1-0, X-0 banked 4pts) — shows the X-0 commitment paying off (a toothless-opponent X-0 per v2.9; Croatia itself was only a moderate -182). ENG-GHA 0-0 = the recurring organized-low-block tail (ESP-CPV/ECU-CUW) — logged, no version (don't whipsaw into draw-leaning). Also added **Rule 5** to Score-Maximizing (per Alok): on a *true coin-flip* with no >50% side, predict **1-1** to maximize EV (modal score → 6, 3pt on any draw, 1pt on any decisive game where a team scores exactly 1) — a wider payout range than a one-sided pick whose 6/4/3 all hinge on the side you can't confidently call. _(Prior: Jun 22 was a +21 validation slate — three exacts, 4/4 outcomes, no version.)_

</details>

---

## ⭐ NORTH STAR — OUTCOME ACCURACY FIRST (read this before anything else)

Getting the **result (W/D/L) right** is the whole game. Correct outcome = a **guaranteed 3 pts** floor and the only gateway to 4 and 6. Wrong outcome = a **ceiling of 1 pt** (usually 0). So flipping one outcome wrong→right is worth ≈ **+3 pts**; refining a scoreline is worth ≈ **+0.5–1**. Always fix the outcome first, then optimize the scoreline.

**Our own data shows where we bleed (through 43 games, outcome accuracy 24/43 = 56%):**
- **Draw picks: 2/8 correct (25%)** — only BEL-EGY & NED-JPN hit; KOR-CZE, CIV-ECU, FRA-SEN, ENG-CRO, GHA-PAN, MEX-KOR all missed.
- **Win picks: 22/35 correct (63%)** — MD2 win picks converting steadily; the misses cluster on one profile: wounded/wasteful favorites that get held to a draw (BEL, URU; see v2.10).

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
- **The Wounded Favorite.** A favorite missing a key attacker, or hit by a red card, vs an organized opponent with a hot keeper. Belgium: Doku out, Ngoy red (66'), Beiranvand 7 saves → 0-0 despite 23 shots. The line (-230) was stale to the absence; the goal threat was gutted. **When a favorite's attack is materially reduced (absence/red card) and the opponent is organized + keeper-strong, the draw is the single most likely outcome — predict 1-1, don't back the win.**
- **The Serial Drawer.** An organized underdog that has *already held a strong team* is a proven draw machine, not a one-off — and is being systematically over-priced against. Cape Verde held Spain 0-0, then drew Uruguay 2-2 (and **scored twice** — so they are not even "toothless"; the X-0 read was doubly wrong). **Once a side has held one favorite, downgrade the next favorite they face toward a draw, and do NOT assume the X-0 against them.**
- **The chronically-wasteful favorite.** Uruguay drew SAU 1-1 then CPV 2-2 — a "favorite" that doesn't finish is a draw risk every game. Weight recent conversion, not just the moneyline.
- **Discipline guard (don't re-trigger the old error).** This is NOT a return to broad draw-leaning (draw picks remain 2/8 = 25%; CIV/FRA/ENG/GHA/MEX punished that). It is a *narrow, profile-gated* draw call: predict the draw ONLY when a concrete wound (key absence / red card / proven serial-holder / misfiring fav) is present. Absent that, keep backing the favorite to win (North Star Rule 1). The EV math: a 1-1 call on a true draw banks 3pts vs the 0 a backed-win takes; but a 1-1 on a game the favorite wins also risks 0–1pt, so only spend it when the wound is real.
- **Objective market-gate (red-team refinement, Jun 22).** The narrative "wound" triggers above are subjective and risk hindsight bias. Add a hard, checkable gate: **only consider the draw when the bookmaker's no-vig draw probability is strictly above both teams' no-vig win probabilities — i.e., the draw is the single most likely outcome (per North Star Rule 2).** If the favorite is a clear modal outcome (e.g. NOR-SEN: NOR 45% vs draw 27%), DO NOT predict the draw no matter how "open" the game feels — back the favorite. The market is a better outcome predictor than our narrative. The wound triggers refine *within* games the market already prices as draw-live; they do not override a clear favorite.
- **Variance caveat — don't over-fit to BEL.** Belgium's 0-0 was driven by a 66' red card, which is variance, not a repeatable signal. The durable lessons from this slate are the *Serial Drawer* (Cape Verde — a pattern across two games) and the *market-gate* (objective). Weight those; treat the red-card case as a one-off, not a reason to fear every elite favorite.
- **Floor logic reaffirmed (v2.9 holds).** When you DO back the favorite to win: X-0 vs a leaky/open opponent that comes out to play (ESP 4-0 SAU ✓), X-1 vs an opponent with a demonstrated goal (NZL scored ✓). Both paid the 4pt floor this slate.

### Validation note — Jun 22 (Groups I & J MD2): the model is calibrated; hold it steady (NO new version)
The best slate of the tournament (**+21, three exacts, 4/4 outcomes, no zeros**) was a clean confirmation of the existing model — not a signal to change it. The whole point of the discipline note below is that confirming slates must NOT trigger a version bump. What fired:
- **X-0 commitment (v2.8/v2.9):** FRA 3-0 IRQ and ARG 2-0 AUT — clear elite-attacking favorites vs sides that came out to play; both kept the clean sheet → both **exact**. ARG also retired the *transitive-threat* fallacy for good: "Austria scored on Jordan ⇒ they'll score on Argentina" was rejected (different opponent, different back line) and Austria blanked. **Lesson: judge the opponent's threat against THIS favorite's defense, not against a common third team.**
- **The X-1 withhold test (v2.9), exact:** ALG 2-1 JOR — Jordan had a *demonstrated* goal (vs Austria) and Algeria is not airtight → we withheld the zero → Jordan scored, Algeria won 2-1 → **exact**. This is the cleanest standalone proof the toothless-vs-threatening test is now a points-positive skill, not a coin flip.
- **The objective market-gate (v2.10), vindicated:** NOR-SEN — no-vig had Norway the 45% modal outcome with the draw only third (27%), so the gate said *back the win, never the 1-1*. Norway won 3-2. The narrative "open game → draw" was correctly overridden by the market.
- **Only residual leak — margin timidity on OPEN games.** NOR 2-1 → 3-2 banked just 3pts because we under-shot a mutual-chase game on BOTH sides (Senegal must-win + Norway's Haaland). This is the *same* timidity logged since GER 7-1 / SWE 5-1, now narrowed to its last hiding place: when the market prices an open, both-teams-score game (BTTS + Over), lift the *winning* margin to 3 and keep the opponent on 1–2 (e.g. 3-1 / 3-2), don't default to 2-1.

### v2.11 — Heavy-Favorite Override on the X-1 Withhold (June 23)
Grading Jun 23 (+11, no zeros, but only 2.75 pts/match) isolated the leak with a clean ≥3-game pattern: the **v2.9 X-1 withhold has now misfired three times — TUN-JPN (0-4), POR-UZB (5-0), COL-COD (1-0) — every time against a clear/heavy favorite, and every time the weak opponent we "protected against" was BLANKED.** We withheld the clean sheet because each opponent had a single "demonstrated goal" (Tunisia's qualifying; Uzbekistan scored on Colombia; DR Congo scored on Portugal), but that goal did not carry against a different, stronger defense. The cost was real: POR should have been 2-0 (4pt floor, not 3), and **COL should have been 1-0 — the 6pt exact we ourselves listed as the alt.** The fix refines, it does not reverse, v2.9:
- **The split is at -200 (no gap): HEAVY = -200 or shorter (≤ -200); MODERATE = longer than -200 (> -200, e.g. -195 to ~-120).** A -190/-195 favorite is MODERATE.
- **The "demonstrated goal" only triggers the X-1 withhold when the favorite is MODERATE (longer than -200) AND genuinely leaks.** GER-CIV (Germany ~-160, no clean sheet in 7), NED-SWE, NZL-EGY, ALG-JOR were all moderate/balanced games where the withhold paid — keep it there.
- **When the favorite is HEAVY (-200 or shorter) and dominant, TAKE THE X-0 regardless of the opponent's prior goal.** A heavy favorite shuts out a weak side far more often than not; a single earlier goal — usually scored against a *softer* opponent or as a one-off — does not predict a goal against THIS, better defense. This is the same **"judge the threat vs THIS back line, not transitively"** principle that produced the ARG-AUT exact (Austria scored on Jordan, blanked vs Argentina). Heavy favorite + weak attack = commit to the zero.
- **The one Jun 23 pick that worked shows the X-0 commitment paying off:** CRO PAN (predicted **2-0**, an X-0 → actual 1-0, banked 4pts) — we did NOT withhold because **Panama was toothless**, so we took the clean-sheet zero. Note this is the **toothless-opponent X-0 (the v2.9 axis), not the heavy-favorite cutoff** — Croatia was only a moderate -182. The lesson it reinforces: take the zero whenever the opponent can't score, independent of the -200 heavy/moderate split.
- **Discipline guard.** This is gated on the favorite's *strength*, an objective, checkable input (the moneyline) — not another narrative tweak. It tightens v2.9's "favorite itself leaks" clause, which we had been reading too loosely (Portugal's 1-1 opener looked "leaky" but a -550 side is not leaky — they scored 5). One axis only: this sets the *scoreline* (will the opponent score?), not the *outcome*.

### Reaffirm (no version) — Jun 23: organized low-block can hold even a -450 favorite to 0-0
ENG 0-0 GHA was an **outcome** miss (we backed England -450 to win 2-0). A disciplined Ghana low-block held them scoreless — England hit the bar and had a header cleared off the line in stoppage. This is the **same recurring tail as ESP 0-0 CPV and ECU 0-0 CUW**: an organized bunker can frustrate even an overwhelming favorite to a draw. **But do NOT over-react into draw-leaning** (draw picks are still 2/8 = 25%) — England nearly won; this is a variance tail, not a reason to fear every heavy favorite. Log it, weight the bunker pattern when an opponent is a *proven* low-block, but keep backing heavy favorites to win (North Star Rule 1). No version change — one game, and the over-correction (drawing heavy favorites) is the more expensive error.

### v2.12 — The Stakes-Asymmetry / Unmotivated-Favourite Override (June 25)
Grading Jun 25 (+15, but only 2/6 outcomes) confirmed a **≥3-game pattern the v2.10 market-gate keeps mis-handling: a favourite with little or nothing to play for loses to a desperate must-win underdog far more than the moneyline implies.** The clean cases: **ECU 2-1 GER** (Germany was seed-locked as group winner regardless of result → zero incentive, fielded a partial mix; we flagged it in-row as "the KOR-RSA shadow, and worse" and STILL backed the -188 fav on the market-gate → lost); **RSA 1-0 KOR** (Jun 24 — Korea needed only a draw → passive → lost); **AUS 2-0 TUR** (Jun 14 — rotated Türkiye). Same motivation-mismatch family on the same slate: **PRY 0-0 AUS** (Australia advancing on a draw → bunkered → 0-0, our PRY-win lost) and **TUR 3-2 USA** (mutual dead rubber — eliminated Turkey played free and beat a rotated USA). The rule:
- **Motivation-asymmetry override of the market-gate.** Before backing a market favourite, check the STAKES. If the favourite is genuinely **unmotivated** — already qualified AND nothing material left to gain (seeding / top-spot locked), or visibly **rotating/resting** — AND the opponent is **must-win / desperate**, do **NOT** back the favourite at the stale line. The moneyline is slow to price full indifference + rotation. Predict the **DRAW**, or lean the desperate side if its edge is concrete. The market-gate assumes both sides are trying; when one isn't, it's invalid.
- **The trigger is objective and checkable pre-game:** (a) is the favourite already through with nothing left to improve? AND (b) is the opponent must-win/desperate? Both yes → motivation-mismatch → downgrade the favourite hard. GER-ECU was textbook on both counts and we had the read in the row — we just didn't act on it. **Acting on the flag is the whole lesson.**
- **"Both content / both dead" → expect open chaos, NOT a quiet 1-1.** PRY-AUS (one side wants only a draw) bunkered to 0-0; TUR-USA (both nothing to play for) exploded 3-2. A dead rubber is not a reliable draw — **Rule 5's 1-1 is for coin-flips between *motivated* sides, not free-for-alls.** For a free-for-all dead rubber, drop confidence further; a one-sided pick on whoever retains marginal motivation (pride, auditioning players, a host's home crowd) is as defensible as 1-1.
- **Don't over-correct — v2.12 fires ONLY on the mismatch profile.** The two clear-favourite + clear-stakes games on this very slate were both **EXACTS**: CIV 0-2 (heavy fav vs a toothless must-win minnow → X-0) and NED 1-3 (motivated fav vs an eliminated-free side → X-1 withhold). When the favourite is **both strong AND motivated**, keep backing the win per the North Star. v2.12 only flips the narrow case of an **unmotivated favourite vs a desperate underdog**. (This is the mirror of v2.10: there the favourite was *wounded*; here it is *indifferent* — both are objective, gated triggers, not vibes.)
- **Eliminated-free tail (from Jun 24) is now CONFIRMED and points-positive:** TUN 1-3 NED — an eliminated side plays free and scores ~1, so withhold the X-0 and lift the winner's margin. Keep applying it.

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

### Rule 5 — True coin-flips (no clear favorite): predict 1-1 to maximize EV, don't commit to one side
When the market shows **no side above ~50%** (a genuine pickem, ±120 both ways) AND a low-scoring/tight game is expected — especially a final-round game where **both teams advance on a draw** — the highest-EV scoreline is **1-1**, not a one-sided X-0/X-1. Why: 1-1 is typically the modal *scoreline* even when one side is the modal *outcome*, and it pays across the widest range — **6 on 1-1, 3 on ANY other drawn result** (0-0/2-2/3-3, all correct-outcome), **and 1pt on any decisive game where either team scored exactly 1** (1-0, 0-1, 2-1, 1-2, 3-1, …, i.e. most low/mid-scoring results). It scores **0 only on a decisive result where neither team scored exactly 1** (2-0, 3-0, 0-2, 0-3, 3-2, …). A one-sided 1-0 has a narrower payout: the 6/4/3 all require *your* side to win, and on the other side's win it banks only 1pt when your team still scored exactly 1 (e.g. you pick 1-0, lose 1-2) and 0 otherwise. Net in a pickem: 1-1's edge is the **3pt-on-any-draw** harvested across the (elevated) draw bucket, plus a broad 1pt decisive floor — not a claim that the one-sided pick is usually a zero. The principle: "when you cannot call the outcome, pick the score that pays across the most scenarios — 6, else 4, else 3, else 1."
- **Boundary (does NOT contradict v2.10 / v2.11):** the market-gate still governs **outcome** selection — when a side IS a clear favorite (≤ ~-150 / >55%), back the win with the X-0 ladder (6→4→3) per v2.11; do NOT use this rule. Rule 5 fires only on genuine pickems.
- **Refines v2.8:** v2.8 said "use X-1 not X-0 in coin-flips" — go one further to **1-1** when the draw bucket is elevated (mutual-advance / two-organized-defenses), because 1-1 adds the 3pt-on-any-draw that an X-1 lacks.
- _Worked example: SUI-CAN Jun 24 — SUI +110 / draw +225 / CAN +250 (no >50% side) + both qualify on a draw, Canada at home → 1-1 over the one-sided 1-0._

### Current score baseline (as of 2026-06-26)
- **155 pts from 59 graded matches** (43.8% efficiency vs 354pt max)
- Exact hits (6pts each): **10 matches** (60/155 = 39% of total score) — HAI-SCT, BEL-EGY, SCO-MAR, BRA-HAI, GER-CIV, FRA-IRQ, ARG-AUT, ALG-JOR, **CUW-CIV, TUN-NED** _(drought broken: 2 on Jun 25)_
- Correct-outcome rate: **33/59 (56%)** — win picks 31/49 (63%), draw picks 2/10 (20%)
- Average per match: **2.63 pts**; target ≥ 3.0 pts/match
- Losses to 0: **10** (+1 Jun 25: TUR 3-2 USA dead-rubber) — …RSA-KOR, **TUR-USA**
- **Jun 25 (+15) split cleanly: the 2 clear-favourite games were EXACTS (CIV, NED); the 4 motivation-mismatch games were all OUTCOME misses** (ECU-GER upset, JPN-SWE draw, PRY-AUS bunker-draw, TUR-USA dead-rubber). The scoreline engine is sharp; the leak is now squarely the **outcome on unmotivated-favourite games → v2.12.** **Standing (last app reading Jun 25): Alok 4th at 141 (internal 140, +1 off-by-one).** After +15 internal is **155 → app ~156**; no fresh screenshot yet. The gap-closer is no longer "hunt exacts" (we did — 2 of them) but **stop donating outcomes on motivation-mismatch games.**

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
| Jun 22 | FRA vs IRQ | 3-0 → 3-0. 🎯 **EXACT.** X-0 commitment + blowout margin on an elite attack vs a leaky weak side. The buried-not-bunkered read (Iraq shipped 4 to Norway) was right. Model fully calibrated for this profile. |
| Jun 22 | ARG vs AUT | 2-0 → 2-0. 🎯 **EXACT.** Messi both goals (outright WC record, 18). Killed the *transitive-threat* fallacy: Austria scoring on Jordan ≠ scoring on Argentina's back line → took the X-0, Austria blanked. Judge threat vs THIS defense. |
| Jun 22 | ALG vs JOR | 2-1 → 2-1. 🎯 **EXACT.** The signature v2.9 proof: Jordan had a demonstrated goal (vs Austria) + Algeria not airtight → withheld the zero → JOR scored, ALG won 2-1. The X-1 withhold is now a points-positive skill. |
| Jun 22 | NOR vs SEN | 2-1 → 3-2. Win (3pts). Market-gate vindicated (backed NOR's 45% modal win over the rejected 1-1; NOT a draw). But under-shot an open mutual-chase game both ways — margin timidity's last hiding place: lift the winner to 3 on BTTS/Over games. |
| Jun 23 | POR vs UZB | 2-1 → 5-0. Win (3pts). Ronaldo brace (1st to score at 6 World Cups). X-1 withhold WRONG — UZB blanked; 2-0 was the 4pt floor. Heavy fav (-550) shuts out a weak side despite their "demonstrated goal." (→ v2.11) |
| Jun 23 | COL vs COD | 2-1 → 1-0. Win (3pts). Muñoz 76'. The X-1 withhold cost the EXACT — our own alt (1-0) was the 6. COD's goal vs Portugal didn't carry vs a tighter defense. Clear fav → take the X-0. (→ v2.11) |
| Jun 23 | CRO vs PAN | 2-0 → 1-0. Win (4pts, PAN 0=0). Budimir sub winner; Modrić's 200th cap. Took the X-0 vs a toothless side and banked the floor — the template that worked. Margin one too high for the exact. (✓ v2.11) |
| Jun 23 | ENG vs GHA | 2-0 → 0-0. Miss (1pt, GHA 0=0). A disciplined Ghana low-block held a -450 England scoreless (bar + off-the-line clearance) — the ESP-CPV / ECU-CUW bunker tail. Variance (England nearly won); don't over-react into draw-leaning. (no version) |
| Jun 24 | BIH vs QAT | 2-0 → 3-1. Win (3pts). BIH won but the X-0 broke — an eliminated Qatar came out and scored. Eliminated-but-free ≠ toothless. (tail) |
| Jun 24 | SUI vs CAN | 1-1 → 2-1. Miss (1pt, CAN 1=1). **Rule 5 validated:** the slight fav won, draw missed, but 1-1 banked 1pt where the one-sided SUI 1-0 would've scored 0. Keep Rule 5 for true pickems. |
| Jun 24 | SCO vs BRA | 0-1 → 0-3. Win (4pts, SCO 0=0). 🟢 X-0 paid — Scotland bunkered and blanked exactly as called; Vini 7'. Margin under by 2 (tight-vs-bunker cost the exact). |
| Jun 24 | MAR vs HAI | 2-0 → 4-2. Win (3pts). X-0 broke again — eliminated Haiti played free and scored twice. Same tail as QAT same day. Margin also under. |
| Jun 24 | RSA vs KOR | 0-1 KOR → 1-0 RSA. **Miss (0pt) — stakes-asymmetry upset.** KOR (-155) needed only a draw, played passive, lost to must-win RSA and got eliminated. A fav playing not-to-lose vs a desperate underdog is an upset risk (cf. AUS-TUR). (tail) |
| Jun 24 | CZE vs MEX | 1-2 → 0-3. Win (3pts). Rotated host still won + clean sheet; the X-1 withhold cost 1pt (CZE blanked → 2-0 was the 4pt floor). |
| Jun 25 | CUW vs CIV | 0-2 → 0-2. 🎯 **EXACT.** Heavy fav (-550) + toothless must-win minnow forced to open up → X-0 at a modest 2-0. The v2.11 template, perfectly applied. Drought broken. |
| Jun 25 | TUN vs NED | 1-3 → 1-3. 🎯 **EXACT.** Eliminated-free tail (TUN played free, scored 1) + NED motivated to score for the goals tiebreaker → X-1 withhold + margin-lift to 3 both landed. The Jun 24 tail drove it. |
| Jun 25 | JPN vs SWE | 2-1 → 1-1. Miss (1pt, SWE 1=1). Backed Japan to win but they only needed a draw → controlled to a 1-1. Low stakes for the favourite should have leaned draw. (→ v2.12 family) |
| Jun 25 | ECU vs GER | 0-1 → 2-1 ECU. **Miss (1pt) — stakes-asymmetry upset, AGAIN.** Germany seed-locked as winner (zero incentive) lost to must-win Ecuador. We flagged it and backed the -188 fav anyway. 3rd such upset. (→ **v2.12**) |
| Jun 25 | PRY vs AUS | 1-0 → 0-0. Miss (1pt, AUS 0=0). The flagged bunker-draw: Australia (through on a draw) parked the bus, Almirón-less Paraguay couldn't break through. A draw call banks 3. (→ v2.12 family) |
| Jun 25 | TUR vs USA | 1-1 → 3-2 TUR. Miss (0pt). Dead rubber EXPLODED — eliminated Turkey played free, beat rotated USA. Rule 5's 1-1 = 0 (a 3-2 has no "1"). Dead rubbers ≠ quiet draws. (→ v2.12) |

---

## How to evolve this file
1. After grading each match, add a one-line takeaway to the lesson log.
2. If the same error repeats across matches, create the next version (v2.2, v2.3, …) describing the rule change and why.
3. Keep the "Active calibration model" section as the current source of truth the predictions apply.
