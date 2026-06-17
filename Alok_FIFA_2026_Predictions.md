# Alok — FIFA World Cup 2026 Pool Betting Predictions

_Canonical predictions tracker, maintained locally (no Google Docs). **Last updated:** 2026-06-17 ~8:05 AM ET — graded Jun 16 (FRA 1-3 miss, IRQ 1-4 NOR ✓outcome, ARG 3-0 ALG ✓outcome, +8 pts → 42); added v2.5 (elite-attacking-favorite exception to MD1 draw gravity); logged Jun 17 slate (POR-COD, ENG-CRO, GHA-PAN, UZB-COL)._

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
| **June 17** | K | POR vs COD | **2 - 0** | Pending | — | LOCKED (v2.5 elite-attacking-fav + Rule 2 X-0 floor). Portugal -360, elite attack (Ronaldo, B.Fernandes, Leão); DR Congo (+1000) organized w/ PL defenders but outclassed. Back the fav win; 0 is plausible vs a debutant-ish underdog. Alt: 3-0. |
| **June 17** | L | ENG vs CRO | **1 - 1** | Pending | — | LOCKED (v2.4 MD1 draw lean). England only -138 vs an elite, experienced Croatia (Modrić, Kovačić, Gvardiol) — modest fav vs strong opponent = the BEL-EGY/NED-JPN draw profile. Alt: narrow ENG 2-1. |
| **June 17** | L | GHA vs PAN | **1 - 1** | Pending | — | LOCKED (v2.4 draw + roster check). Ghana only ~-110 and weakened — **Partey out (visa denied)**; Panama organized, limited in open play. Weakened modest fav vs solid underdog = draw. Alt: narrow GHA 2-1. |
| **June 17** | K | UZB vs COL | **2 - 0** | Pending | — | LOCKED (v2.5 + Rule 2). Colombia -250, deep attack (L.Díaz, James, Cucho) and *altitude-comfortable* (Bogotá) at the Azteca; Uzbekistan organized debutant (Cannavaro) but outgunned. Fav win, 0 plausible. Alt: 1-1 (organized-debutant frustration risk). |

---

## 2. Running Scorecard

| Metric | Value |
| :--- | :--- |
| Graded predictions | 19 |
| Correct outcome (W/D/L) | 8 of 19 (USA; HAI–SCT; GER; NED–JPN; SWE; BEL–EGY; IRQ–NOR; ARG–ALG) |
| Exact scoreline | 2 of 19 (HAI 0-1 SCT 🎯; BEL 1-1 EGY 🎯) |
| **Total score** | **42 / 114** (…34 + Jun 16: 1+3+4) |
| Recurring error | **Jun 16 flipped the MD1 draw pattern:** all three favorites WON — FRA 3-1 (beat *elite* Senegal), NOR 4-1, ARG 3-0 (two by 3+). Common thread: elite attacking favorites, fully fit, with in-form superstars (Mbappé/Haaland/Messi). v2.4's broad draw-default was too wide — it cost us FRA-SEN (predicted 1-1, France won). → **v2.5** carves out the elite-attacking-favorite exception and stops over-capping their margins. The X-0 floor rule paid (ARG-ALG → 4pts). |

_Codes: CUW = Curaçao, CIV = Côte d'Ivoire, TUR = Türkiye, ECU = Ecuador, RCH = Chile, RSA = South Africa, PRY = Paraguay, BIH = Bosnia._
