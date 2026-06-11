# Bracket 26 — FIFA World Cup 26 Predictor

An interactive prediction bracket for the 2026 FIFA World Cup (Canada · Mexico · United States, June 11 – July 19, 2026). Predict all 104 matches, watch the knockout draw build itself, then grade your bracket against the real tournament.

**Open `index.html` to start. See `user-guide.html` for a visual walkthrough.**

---

## Features

### Group stage
- **All 12 real groups (A–L)** from the official December 5, 2025 draw, including the March 2026 playoff winners (Czechia, Bosnia & Herzegovina, Sweden, Iraq, Curaçao, DR Congo).
- **Tap-to-score** — every score box is a button: first tap sets 0, each tap adds a goal, tapping past 9 clears it. A 0–0 prediction takes two taps.
- **Hover reset** — hover any match row that has a score and a small × appears at the right edge to wipe just that match.
- **Live standings** — points, W/D/L, goal difference compute instantly with official tiebreakers (points → GD → goals → ranking). Top two highlight green when a group completes; a qualifying third highlights amber.
- **Best third-placed teams** — once all 12 groups are scored, the twelve 3rd-place teams are ranked by the official criteria; the top 8 advance.

### Knockout bracket
- **Official match map (M73–M104)** — the real Round-of-32 slot structure, through Round of 16, quarterfinals, semifinals, third-place match and the July 19 final in New Jersey.
- **Auto-populating** — group winners, runners-up, and the eight best thirds drop into their slots the moment groups complete. Third-place routing respects the official slot constraints (the real tournament uses FIFA's Annex C matrix for exact pairings).
- **Tap to advance** — click a team to send it through; click again to unpick. Downstream picks invalidate automatically if you change an earlier result.
- **Fit-to-screen** — the full 9-column bracket scales to your window. No horizontal scrolling.
- **Champion banner** — picking the final's winner triggers a celebration banner with confetti.

### Auto-fill simulation
One click fills every *remaining* prediction (your own entries are never touched):
- Group scores are sampled from a Poisson model: expected goals = `1.15 + (opponent rank − own rank) / 40`, clamped 0.2–3.2, using approximate FIFA rankings.
- Knockout picks favor the higher-ranked team 82% of the time, with an 18% upset chance.
- Every run produces a different, plausible tournament.

### Prediction vs. Actual results
- The **EDITING toggle** (tab row, right side) switches between *My prediction* and *Actual results* — two fully separate datasets.
- In Actual mode, set scores show **gold borders** so reality is never confused with guesses, and auto-fill is disabled.

### Scorecard
Grades your prediction against entered real results:
| What | Points |
|---|---|
| Exact group score | 3 |
| Correct group outcome (W/D/L) | 1 |
| Team correctly through to R32 | +1 each |
| …to Round of 16 | +2 each |
| …to Quarterfinals | +4 each |
| …to Semifinals | +8 each |
| …to the Final | +16 each |
| Champion | +32 |
Knockout credit is path-independent — if your team gets there, you score.

### Path to Glory
Click any team's row in a standings table → an overlay shows their predicted story: three group games with W/D/L badges, predicted finish, and every knockout round until elimination — or the title.

### Sharing (appears when your bracket is 100% complete)
- **SHARE** — native share sheet on mobile, clipboard on desktop. Text summary with flag emoji: champion, final, semifinalists.
- **CARD** — downloads a 1200×630 PNG of your prediction (champion flag, final, semifinalists) sized for group chats.

### Persistence
Everything (both datasets) saves to your browser automatically and survives reloads. **CLEAR** wipes only the active mode's data, with confirmation.

---

## Files
| File | Purpose |
|---|---|
| `index.html` | The predictor app |
| `user-guide.html` | Illustrated user guide |
| `README.md` | This file |

## Data & design notes
- Teams, groups, fixtures and bracket structure reflect the official draw and schedule; team rankings (used only for simulation) are approximate.
- Flags load from flagcdn.com at runtime.
- Original visual identity (paper/ink palette, host-nation tricolor, Anton + Archivo) — intentionally not FIFA's protected brand assets.
