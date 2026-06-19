# Alok — FIFA World Cup 2026 Pool Betting Predictions

_Canonical predictions tracker, maintained locally (no Google Docs). **Last updated:** 2026-06-18 — re-prediction pass via ESPN/Playwright. **Date fix (ESPN ET calendar):** MEX-KOR is **Jun 19** 1 AM ET (was wrongly on Jun 18); BRA-HAI & TUR-PAR are **Jun 20** early-AM ET (were on Jun 19). Fixtures re-slotted to true ET dates → Jun 18: CZE-RSA, SUI-BIH, CAN-QAT · Jun 19: MEX-KOR, USA-AUS, SCO-MAR · Jun 20: BRA-HAI, TUR-PAR. Odds re-verified (≈unchanged). **CAN-QAT softened 2-0→2-1** (Qatar held SUI 1-1 and scored — organized, so v2.6 says don't bet the X-0 zero). All pending; first KO Jun 18 4 PM ET. Prior: graded Jun 17 (+4 → 46), added v2.6 (Matchday-2 regime shift)._

> Calibration logic for these predictions lives in **`lessons.md`**. Read both files together; this file holds fixtures/results, `lessons.md` holds the prediction algorithm.

---

## 1. Match Tracker & History Log

| Date (2026) | Group | Fixture | Our Prediction | Actual Result | Score | Outcome / Review Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| June 11 | A | MEX vs RSA | 1 - 0 | 2 - 0 | **4** | **Miss.** Early 9th-min breakthrough + red cards forced RSA open; unaccounted 2nd goal. _(Winner ✓, RSA goals 0=0 ✓)_ |
| June 11 | A | CRC vs RCH | 1 - 1 | 2 - 1 | **1** | **Miss.** Open transition match vs the projected rigid tactical draw. _(RCH goals 1=1 ✓, wrong outcome)_ |
| June 12 | B | CAN vs BIH | 2 - 0 | 1 - 1 | **0** | **Miss.** Roster anomaly: A. Davies unused sub; set-piece frailty broke clean-sheet ceiling. |
| June 12 | D | USA vs PRY | 2 - 1 | 4 - 1 | **4** | **Win (wrong margin).** Host-nation adrenaline; early 7th-min own goal crushed PRY low block. _(Winner ✓, PRY goals 1=1 ✓)_ |
| June 13 | B | QAT vs SUI | 0 - 2 | **1 - 1** | **0** | **Miss.** Strong favorite Switzerland (-350) couldn't break Qatar's block; Embolo pen (17'), Khoukhi equalized in 2H stoppage time for Qatar's first-ever WC point. Even softened to 0-2 we still backed a SUI win — MD1 favorites are dropping points. |
| June 13 | C | BRA vs MAR | 1 - 0 | **1 - 1** | **1** | **Miss.** Roster check (Neymar out) was right, but we still gave Brazil the win; Saibari put Morocco ahead (21'), Vinícius equalized (32'). Weakened favorite vs strong opponent = draw. _(BRA goals 1=1 ✓, wrong outcome)_ |
| June 13 | C | HAI vs SCT | 0 - 1 | **0 - 1** | **6** | **WIN (exact).** 🎯 McGinn (28') the lone goal. Disciplined 1-0 favorite call (softened from 0-2 via v2.1) nailed it — clear mismatch vs a genuinely weak side. |
| June 14 | D | AUS vs TUR | 1 - 2 | **2 - 0 (AUS)** | **0** | **Miss.** Türkiye rested Yıldız; organized Australia won to nil (Irankunda, Metcalfe). Backed the wrong side — MD1 underdog upset. |
| June 14 | E | GER vs CUW | 4 - 0 | **7 - 1** | **3** | **Win (wrong margin).** Clear-mismatch call right; badly under-shot the blowout (Havertz ×2 + Nmecha, Schlotterbeck, Musiala, Brown, Undav; Comenencia for CUW). → v2.3 blowout ceiling. |
| June 14 | F | NED vs JPN | 1 - 1 | **2 - 2** | **3** | **Win (wrong margin).** 🎯 Outcome nailed — v2.2 draw lean validated. Van Dijk (51') & Summerville (64') for NED; Nakamura + Ogawa (88') for Japan. |
| June 14 | E | CIV vs ECU | 0 - 0 | **1 - 0 (CIV)** | **1** | **Miss.** Defensive-floor read right (0-0 deep into the 90th) but Amad Diallo nicked a 90' winner. Even floor games can break 1-0 late — don't default to 0-0. → v2.3. _(ECU goals 0=0 ✓, wrong outcome)_ |
| June 14 | F | SWE vs TUN | 1 - 0 | **5 - 1** | **3** | **Win (wrong margin).** Over-softened on Tunisia's qualifying clean sheets (earned vs weak CAF opp.); Sweden ran riot (Ayari ×2, Isak, Gyökeres). → v2.3. |
| June 15 | H | ESP vs CPV | 4 - 0 | **0 - 0** | **1** | **Miss (big).** Cape Verde debutants held Spain scoreless — 27 SHOTS, 7 on target, Torres hit the bar; keeper Vozinha brilliant. Blowout call (v2.3) wrong: an *organized low-block* debutant ≠ a leaky one. → v2.4. _(CPV goals 0=0 ✓, wrong outcome)_ |
| June 15 | G | BEL vs EGY | 1 - 1 | **1 - 1** | **6** | **WIN (exact).** 🎯 v2.2 draw lean nailed it again. Ashour stunner (19') for Egypt; Lukaku forced a Hany OG (66') 22s after coming on. MD1 favorite vs organized Salah side = draw. |
| June 15 | H | SAU vs URU | 0 - 1 | **1 - 1** | **1** | **Miss.** Uruguay (-220, fully fit) couldn't win — Al Amri put Saudi ahead, Maxi Araújo equalized late. The "class-above fully-fit favorite → narrow win" exception failed on MD1. → v2.4. _(URU goals 1=1 ✓, wrong outcome)_ |
| June 15 | G | IRN vs NZL | 1 - 0 | **2 - 2** | **0** | **Miss.** Low-scoring lean wrong — open game. Elijah Just brace for NZ; Rezaeian & Mohebi for Iran. Another MD1 favorite held. → v2.4. |
| June 16 | I | FRA vs SEN | 1 - 1 | **3 - 1 (FRA)** | **1** | **Miss.** Backed the draw on an elite, fully-fit favorite vs an elite opponent — wrong. Mbappé brace (now record WC scorer for FRA) + Barcola; France's class told. MD1 draw gravity over-applied to an elite attacking side. _(SEN goals 1=1 ✓, wrong outcome)_ → v2.5. |
| June 16 | I | IRQ vs NOR | 0 - 2 | **1 - 4 (NOR)** | **3** | **Win (wrong margin).** Norway win nailed; margin far too timid. Haaland brace + Østigård + Hussein OG; Iraq wasn't "disciplined" — leaked vs a real attack. _(winner ✓, both goal counts miss)_ → v2.3/v2.5. |
| June 16 | J | ARG vs ALG | 1 - 0 | **3 - 0 (ARG)** | **4** | **Win (wrong margin).** 🎯 X-0 floor rule paid off (ALG 0=0 ✓ → 4pts). Messi hat-trick (ties Klose, 16 WC goals). Margin too timid for the exact — elite fav buried a mid-tier side. _(winner ✓ + ALG 0=0 ✓)_ → v2.5. |
| June 17 | K | POR vs COD | 2 - 0 | **1 - 1** | **0** | **Miss.** Elite attacking favorite HELD on MD1 — J. Neves struck 6', but Wissa equalized 45+5' and DR Congo held. v2.5's "elite-attacking-fav → win" exception failed its first test: Ronaldo's Portugal couldn't break an organized debutant. → v2.6. |
| June 17 | L | ENG vs CRO | 1 - 1 | **4 - 2 (ENG)** | **0** | **Miss (big).** Backed the draw on a modest fav (-138) vs elite Croatia — England blew it open. Kane brace (12' pen, 42'), Bellingham (47'), Rashford (85'); Baturina & Musa for CRO. MD1 draw gravity badly over-applied. → v2.6. |
| June 17 | L | GHA vs PAN | 1 - 1 | **1 - 0 (GHA)** | **1** | **Miss.** 0-0 into the 90th (the CIV-ECU floor pattern again), then Yirenkyi won it 90+5'. Weakened-fav draw lean nearly right; a late winner made it 1-0. _(GHA goals 1=1 ✓, wrong outcome)_ |
| June 17 | K | UZB vs COL | 2 - 0 | **1 - 3 (COL)** | **3** | **Win (wrong margin).** Fav win nailed but X-0 floor missed — Uzbekistan scored (Fayzullaev 60'). Muñoz (40'), Díaz (65'), Campaz (90+9') for Colombia. Organized debutant got on the board; don't auto-assume the 0. _(winner ✓, both goal counts miss)_ |
| **June 18** | A | CZE vs RSA | **1 - 0** | Pending | — | LOCKED (v2.6 MD2; Rule 2 X-0 floor). Czechia modest fav (-125); South Africa down TWO suspensions (Zwane 3-match, Sithole 1-match, both red vs MEX). MD2 — draw gravity lifts; weakened opponent → back narrow CZE win, RSA plausibly blanks. Alt: 2-1. |
| **June 18** | B | SUI vs BIH | **2 - 1** | Pending | — | LOCKED (v2.6 MD2). Switzerland (-180) the clearer side after a settling MD1; Bosnia missing Čelik, Tabaković & Kolašinac doubtful. MD2 favorites convert more than MD1 — back the SUI win. Alt: 2-0. |
| **June 18** | B | CAN vs QAT | **2 - 1** | Pending | — | LOCKED (v2.6 MD2 + HOST). **Canada host at home (BC Place, Vancouver), -340 (ESPN)**; **Davies a game-time doubt** (missed opener — do NOT assume he returns). Qatar held SUI 1-1 and scored on MD1 → organized + finds the net, so v2.6 says skip the X-0 zero. **Softened 2-0 → 2-1** to protect the 3pt floor without betting Qatar blanks. Alt: 2-0 (if Davies starts). |
| **June 19** | A | MEX vs KOR | **1 - 1** | Pending | — | LOCKED (v2.6 + HOST caution). Near pick-'em — Mexico host at home (Estadio Akron, Guadalajara) but only **+105 (ESPN)**; Korea organized. Host edge offset by a genuinely even matchup → lean draw. **(1 AM ET Jun 19 — was misdated Jun 18.)** Alt: narrow MEX 2-1. |
| **June 19** | D | USA vs AUS | **2 - 1** | Pending | — | LOCKED (v2.6 MD2 + HOST, v2.0). **USA host at home (Lumen Field, Seattle), -170 (ESPN)**, fresh off a 4-1 rout; Pulisic (calf) a game-time doubt but deep attack. Australia organized (beat TUR 2-0) — back host win, narrow. Alt: 2-0. |
| **June 19** | C | SCO vs MAR | **1 - 1** | Pending | — | LOCKED (v2.6 MD2). Morocco narrow fav (**-135, ESPN**) but Scotland organized and coming off a 1-0 win; McKenna a calf doubt. Tight, evenly-matched MD2 → lean draw. Alt: narrow MAR 1-0. |
| **June 20** | C | BRA vs HAI | **3 - 0** | Pending | — | LOCKED (v2.6 MD2 + v2.3 blowout + Rule 2). Brazil heavy fav (**-1000, ESPN**) at full tilt after the MAR draw; Haiti leaky, lost 0-1 to SCO. Elite attack vs a beatable minnow → back a real margin, Haiti blanks. **(12:30 AM ET Jun 20 — was on Jun 19.)** Alt: 2-0. |
| **June 20** | D | TUR vs PAR | **2 - 1** | Pending | — | LOCKED (v2.6 MD2). Türkiye narrow fav (**-105, ESPN**); Yıldız a doubt but Çalhanoğlu & Güler fit. Paraguay missing Caballero, Sosa doubtful, lost 1-4 MD1. Back TUR to bounce back. **(3 AM ET Jun 20 — was on Jun 19.)** Alt: 1-1 (coin-flip risk). |

---

## 2. Running Scorecard

| Metric | Value |
| :--- | :--- |
| Graded predictions | 23 |
| Correct outcome (W/D/L) | 10 of 23 (MEX–RSA; USA–PRY; HAI–SCT; GER; NED–JPN; SWE; BEL–EGY; IRQ–NOR; ARG–ALG; UZB–COL) |
| Exact scoreline | 2 of 23 (HAI 0-1 SCT 🎯; BEL 1-1 EGY 🎯) |
| **Total score** | **46 / 138** (…42 + Jun 17: 0+0+1+3) |
| Recurring error | **Jun 17 whipsawed both ways — every MD1 prediction missed the outcome.** We backed the elite-fav WIN (POR 2-0, per v2.5) and got a 1-1 DRAW; we backed the DRAW (ENG 1-1, per v2.4) and got a 4-2 BLOWOUT. The two models gave opposite errors on the same slate, so neither MD1 rule is reliable. **But all four Jun 17 games were Matchday 1; the calendar has now rolled to Matchday 2.** The whole "MD1 draw gravity" body of evidence (v2.2/v2.4/v2.5) is regime-specific to openers — rust, caution, first-game variance. → **v2.6** declares the MD2 regime shift: drop the broad draw default, back the better/fitter side to convert, and use the host + blowout + X-0 rules normally. |

_Codes: CUW = Curaçao, CIV = Côte d'Ivoire, TUR = Türkiye, ECU = Ecuador, RCH = Chile, RSA = South Africa, PRY = Paraguay, BIH = Bosnia._
