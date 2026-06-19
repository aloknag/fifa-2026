# Alok — FIFA World Cup 2026 Pool Betting Predictions

_Canonical predictions tracker, maintained locally (no Google Docs). **Last updated:** 2026-06-19 — **STRATEGY RESET: OUTCOME ACCURACY FIRST.** Our draw picks are 2/7 (29%) vs win picks 10/19 (53%) — draws are the leak. New standing rule (see `lessons.md` North Star): back the bookmaker favorite to win; predict a draw ONLY when the draw is the single most likely result. Applied to the pending slate → **SCO-MAR flipped from 1-1 draw to a Morocco win.** Also fixed historical labels (KOR-CZE mislabel; MEX-RSA was a 4pt correct-outcome, not a "miss"; UZB-COL notation). Score **55/162** from 27 graded. Pending: USA-AUS, SCO-MAR, BRA-HAI (Jun 19), TUR-PAR (Jun 20). Prior: graded Jun 18–19 (+9), added v2.6/v2.7 (MD2 regime + margin)._

> Calibration logic for these predictions lives in **`lessons.md`**. Read both files together; this file holds fixtures/results, `lessons.md` holds the prediction algorithm.

---

## 1. Match Tracker & History Log

| Date (2026) | Group | Fixture | Our Prediction | Actual Result | Score | Outcome / Review Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| June 11 | A | MEX vs RSA | 1 - 0 | 2 - 0 | **4** | **Win (wrong margin).** Correct side (MEX win) + RSA 0=0 → 4pts; red cards opened a 2nd goal. _(Winner ✓, RSA 0=0 ✓)_ |
| June 11 | A | KOR vs CZE | 1 - 1 | 2 - 1 | **1** | **Miss.** _(Logged as "CRC vs RCH" in error — actual Group A fixture was KOR 2-1 CZE; score unchanged.)_ Predicted a draw; Korea won. _(CZE 1=1 ✓, wrong outcome)_ |
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
| June 17 | K | UZB vs COL | 0 - 2 | **1 - 3 (COL)** | **3** | **Win (wrong margin).** Colombia (the 0-2 favorite pick) won ✓; X-0 floor missed — Uzbekistan scored (Fayzullaev 60'). Don't auto-assume the 0 vs an organized debutant. _(winner ✓)_ |
| June 18 | A | CZE vs RSA | 1 - 0 | **1 - 1** | **1** | **Miss.** Sadilek struck 6' (earliest goal of the WC so far), but wasteful Czechia were pegged back — Mokoena pen 83' after a Sulc handball. A modest MD2 fav (-125) still failed to beat a suspension-depleted RSA; late-pen variance. _(CZE goals 1=1 ✓, wrong outcome)_ |
| June 18 | B | SUI vs BIH | 2 - 1 | **4 - 1 (SUI)** | **4** | **Win (wrong margin).** v2.6 fav-converts ✓ and BIH 1=1 floor → 4pts. Five goals in the last 23' (Manzambi ×2, Vargas, Xhaka pen); margin under-shot again. _(winner ✓ + BIH 1=1 ✓)_ → v2.7. |
| June 18 | B | CAN vs QAT | 2 - 1 | **6 - 0 (CAN)** | **3** | **Win (wrong margin).** Host blowout — J. David hat-trick + Larin, Saliba, OG; biggest CONCACAF WC win. We softened 2-0→2-1 fearing Qatar would score; the abandoned X-0 would have paid **4pts** (QAT 0=0). Host adrenaline + margin timidity. → v2.7. |
| June 19 | A | MEX vs KOR | 1 - 1 | **1 - 0 (MEX)** | **1** | **Miss.** Host Mexico edged it — Romo finished a Kim Seung-gyu blunder; MEX top Group A. Pickem draw-lean missed: don't auto-draw a host even at +105. _(MEX goals 1=1 ✓, wrong outcome)_ → v2.7. |
| **June 19** | D | USA vs AUS | **2 - 1** | Pending | — | LOCKED (v2.6 MD2 + HOST, v2.0/v2.7). **USA host at home (Lumen Field, Seattle), -170 (ESPN)**, fresh off a 4-1 rout amid the host-blowout wave (CAN 6-0, MEX 1-0); Pulisic (calf) a game-time doubt but deep attack. Australia organized (beat TUR 2-0, clean sheet) caps the margin — back a host win. Alt: 3-1 (host blowout) / 2-0 (X-0). |
| **June 19** | C | SCO vs MAR | **0 - 1 (MAR)** | Pending | — | **CHANGED 1-1 draw → Morocco win (outcome-first).** Morocco **-135 (ESPN)**, unbeaten in 30, the better/organized side; Scotland organized too → low total, but Morocco win is the modal outcome (~50% vs ~33% draw). Back the favorite, not the draw. Alt: 1-1. |
| **June 19** | C | BRA vs HAI | **3 - 0** | Pending | — | LOCKED (v2.3 blowout + v2.7 margin + Rule 2). Brazil heavy fav (**-1000, ESPN**) at full tilt after the MAR draw (Neymar still out, but Cunha/Endrick/Vinícius); Haiti organized but beatable (lost 0-1 to SCO, scored 0). Elite attack + the don't-under-shot lesson → back a real margin, Haiti blanks. **(9 PM ET Jun 19, Philadelphia.)** Alt: 4-0 / 2-0. |
| **June 20** | D | TUR vs PAR | **2 - 1** | Pending | — | LOCKED (v2.6 MD2). Türkiye narrow fav (**-105, ESPN**); Yıldız a doubt but Çalhanoğlu & Güler fit, and they had 30 shots vs AUS. Paraguay missing Caballero, Sosa doubtful, lost 1-4 MD1 — both desperate must-win → open game. **(12 AM ET Jun 20, Santa Clara.)** Alt: 1-1 (coin-flip risk) / 2-0. |

---

## 2. Running Scorecard

| Metric | Value |
| :--- | :--- |
| Graded predictions | 27 |
| Correct outcome (W/D/L) | **12 of 27 (44%)** — MEX–RSA; USA–PRY; HAI–SCT; GER; NED–JPN; SWE; BEL–EGY; IRQ–NOR; ARG–ALG; UZB–COL; SUI–BIH; CAN–QAT |
| — by pick type | **Win picks 10/19 (53%) · Draw picks 2/7 (29%)** ← draws are the leak |
| Exact scoreline | 2 of 27 (HAI 0-1 SCT 🎯; BEL 1-1 EGY 🎯) |
| **#1 priority** | **Outcome accuracy.** Back favorites; predict draws only when the draw is the single most likely result. Each wrong→right outcome ≈ +3 pts; scoreline tweaks ≈ +0.5–1. |
| **Total score** | **55 / 162** (…46 + Jun 18–19: 1+4+3+1) |
| Recurring error | **Margin timidity is now the dominant leak.** v2.6 (back MD2 favorites) is broadly validated — SUI, CAN, MEX all won (3 of 4 favorites; only the depleted-but-stubborn CZE 1-1 escaped), and our one draw-lean (MEX-KOR +105) cost us. But three of the last four wins were "right side, margin far too low": **SUI 2-1→4-1, CAN 2-1→6-0**, and earlier GER/SWE/NOR. **Host adrenaline is producing blowouts** (CAN 6-0, USA 4-1, MEX win) — we under-projected CAN and even abandoned the X-0 that would have paid. → **v2.7** lifts host/strong-favorite margins (project 3+ vs weak/leaky/depleted sides) and reaffirms the X-0 floor for hosts vs weak opponents. Draws now reserved for genuine two-organized-defense pickems (SCO-MAR). |

_Codes: CUW = Curaçao, CIV = Côte d'Ivoire, TUR = Türkiye, ECU = Ecuador, CZE = Czechia, KOR = South Korea, MAR = Morocco, COD = DR Congo, RSA = South Africa, PRY = Paraguay, BIH = Bosnia._
