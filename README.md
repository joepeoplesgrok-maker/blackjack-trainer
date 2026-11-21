# Blackjack & Card Counting Trainer Pro

A self-contained, mobile-first Progressive Web App (PWA) for learning Basic Strategy, Hi-Lo card counting, Illustrious 18 & Fab 4 deviations, and optimal bet sizing across 1, 2 (Double Deck), 4, 6, and 8-deck shoes.

## Features
- **Table Play**: Full Blackjack with CSPRNG Fisher-Yates shuffling, burn card, deck-accurate penetration, exact $0.50 payouts, Insurance / Even Money, Late Surrender, live Count HUD, and Strategy/Deviation Coach.
- **Speed Count**: 52-card Hi-Lo flashcard drill (1, 2, or 3 cards at a time; manual or auto-deal). Best time and cards/sec are saved.
- **Strategy Drill**: Rapid-fire Basic Strategy and Illustrious 18 / Fab 4 trainer, with an optional countdown per decision.
- **Charts**: Dynamic deck-accurate strategy cards (2D, 6D, 8D) and the Hi-Lo / Kelly / Wonging reference.
- **Stats**: Session and lifetime accuracy by hard / soft / pairs / deviations / bets / insurance, a bankroll chart, most-missed situations, and a mistake-review quiz.
- **Risk Tools**: Estimated win rate per hour, standard deviation, N0, risk of ruin, and Kelly / half-Kelly bet sizing (approximations — always labeled as estimates).
- **How It Works**: In-app guide covering every strategy, index, toggle, and mode.
- **Settings → Features**: Every advanced tool can be turned on or off individually. Choices persist in `localStorage` (`bj_trainer_v7`).
- **Offline Ready**: Installable via **Add to Home Screen** on iOS and Android.

## Table rules (implicit)
- American peek for dealer blackjack (Ace or 10-up). Insurance / Even Money are offered only when the dealer shows an Ace.
- Natural blackjack pays **3:2** (no 6:5 option).
- Late surrender, when enabled, is on the first two cards of a single unsplit hand.
- Split aces receive one card each and cannot be hit, doubled, or resplit (no RSA).
- A two-card 21 after a split is paid as a regular win, not a blackjack.
- If the cut-card shoe is exhausted mid-hand (rare at these penetrations), a **new shoe is shuffled to finish dealing**. The running count resets for the fresh shoe; cards already on the table, including a hidden hole card from the previous shoe, are not carried into the new count. The new shoe then continues for later hands.

## Feature guide (v8)

The **live shoe and discard bars** sit beside the table during Table Play (on by default). The Shoe bar empties and the Discard bar fills as cards come out, including other seats; both reset on a shuffle. A red mark on the Shoe bar is the cut card. Exact leftover decks stay hidden unless you enable “Show exact decks remaining.” Tap the bars to estimate decks remaining (within 0.5 decks). Feedback shows the true leftover decks and how your guess would have changed the true count. An optional prompt can ask every 5, 10, or 15 hands (off by default). The standalone **Deck Estimate Drill** is still a separate Features toggle.

## Feature guide (v7)

Open **How It Works** in the header for the full write-up. The short version:

- **Basic strategy** follows the in-app, deck-accurate charts (Wizard of Odds family).
- **Hi-Lo**: low cards (2–6) +1, 7–9 0, 10s and Aces −1. True count is the running count divided by unseen decks. Rounding can be exact (default, same as v6), floor, truncate toward 0, or `Math.round`. The chosen mode is used everywhere: HUD, deviations, bet ramp, and quizzes.
- **Illustrious 18** (when the I18 toggle is on): insurance / even money at a deck-aware index (1D +1.5, 2D +2.5, 4–8D +3); 16 vs 10 stand at TC ≥ 0 (when surrender is not available); 15 vs 10 stand at TC ≥ +4 (no surrender); 10,10 vs 5 / 6 split at +5 / +4; 10 vs 10 double at +4; 12 vs 3 stand at +2; 12 vs 2 stand at +3; 11 vs A double at +1 (6D S17) or hit at ≤ −1 when basic is double; **9 vs 2** double at +1 (6D) or **hit at TC < 0 (2D)** — this 2-deck play now uses the true count, not the running count; 10 vs A double at +4 (6D S17) or +3 (2D / H17); 9 vs 7 double at +3; 16 vs 9 stand at +5; 13 vs 2 hit at ≤ −1; 12 vs 4 hit at ≤ 0; 12 vs 5 hit at ≤ −2; 12 vs 6 hit at ≤ −1; 13 vs 3 hit at ≤ −2.
- **Fab 4** (when on, late surrender allowed): 14 vs 10 (including 7,7) at TC ≥ +3; 15 vs 10 at TC ≥ 0; 15 vs 9 at TC ≥ +2; 15 vs A at TC ≥ +1 (S17) or ≥ −1 (H17).
- **Bet ramp** (default): 1 unit at TC ≤ 1, then +1 unit per true count, capped at your spread (default 1–12). An optional grader marks each bet correct / too high / too low.
- **Quizzes & drills**: optional running/true-count quizzes, a discard-tray deck-estimate (graded within 0.5 decks), the Speed Count and Strategy Drill modes, and optional timed decisions (timeout counts as a miss).
- **Risk tools**: EV ≈ 0.5% per TC minus the rules’ house edge; per-hand variance ≈ 1.3 units²; true-count frequencies are simulated from this app’s shoe and penetration. Kelly fraction = edge / 1.3. These are estimates, not a guarantee.
- **Other seats** play basic strategy from the same shoe (their cards count). **Heat hints** warn about a >2× bet jump or a leap from ≤2 units to the top of the spread.

Default toggles keep the core table clean: I18, Fab 4, insurance index, and the bet ramp stay on (they power the existing coach and HUD). Bet grading, count quizzes, deck estimate, timed decisions, other seats, and heat hints start off. Speed Count, Strategy Drill, Stats, and Risk Tools stay in the mode menu until you hide them.

Turning a feature off hides its UI and skips its logic.

## Changelog

### v8
- Live **Shoe** and **Discard** bars on the Table Play felt (labeled, compact). The shoe empties and the discard fills as cards are dealt — including other seats — and both reset when the shoe is shuffled. A red cut-card mark sits on the shoe bar.
- Exact leftover decks stay hidden by default so estimation stays a skill. An optional assist can show the true leftover decks on the bars.
- Tap the bars at any time to estimate decks remaining (0.5-deck tolerance). Feedback includes the actual decks left and the true-count impact of your guess. Optional auto-prompts every N hands (off by default).
- Settings → Features: “Live shoe & discard bars” is on by default; “Show exact decks remaining” and the prompt interval start off. The separate deck-estimation drill is unchanged.
- Service worker cache bumped to `bj-trainer-v8`.

### v7
- Configurable unit size and bet spread with a TC → units ramp, plus an optional bet-grading mode.
- Optional count quizzes, a discard-tray deck-estimate drill, speed-count best times, and timed strategy-drill decisions.
- Complete I18 / Fab 4 / insurance index coverage, consistent TC rounding (exact / floor / truncate / round), and I18 #10 (2D 9 vs 2) now keys off **TC < 0** rather than the running count.
- Session + lifetime stats, bankroll chart, most-missed list, and mistake review. Versioned `bj_trainer_v7` storage with a reset button.
- Risk tools: estimated EV/hr, SD/hr, N0, risk of ruin, Kelly and half-Kelly.
- Optional 1–6 other seats (basic strategy, same shoe) and educational heat hints.
- Every advanced feature is individually toggleable under Settings → Features; choices persist. A **How It Works** mode explains each strategy, index, toggle, and mode.
- Layout: long split hands scroll from the left so the first card is never clipped; short-landscape hand titles stay on one line above the result banner; header mode labels (`Table Play`, `Speed Count`, `Strategy Drill`, `Charts`, `Stats`, `Risk Tools`, `How It Works`) fit the dropdown.
- Service worker cache bumped to `bj-trainer-v7`.

### v6
- Hi-Lo count tags sit under each card's own rank/suit index in the visible left strip, so they no longer cover the next overlapping card's corner label.
- Round-result banner net includes insurance (win or loss) and even money, e.g. a lost $12.50 insurance on a $25 hand reports **-$37.50**.
- Short phone landscape keeps compact per-hand WIN/LOSE labels in the hand title (needed after a split).
- Service worker (`bj-trainer-v6`) falls back to `index.html` only for navigation requests; other cache misses surface a network error.
- All form controls, including the header mode dropdown, use a 16px font so iOS Safari does not zoom on focus.

### v5
- Fixed iOS / iPad Safari blank `<select>` labels (explicit dark background, light text, `appearance: none`, custom arrow).
- Illustrious 18: 16 vs 10 now stands at **TC ≥ 0**; 12 vs 4 now hits at **TC ≤ 0** (same raw-TC comparisons as the other I18 entries).
- Added `icon-192.png` and a padded `icon-maskable-512.png` (content inside the 80% safe zone). Manifest lists 192/512 as `any` and the padded 512 as `maskable`. Orientation is `any`.
- `formatMoney` now formats negatives as `-$12.50`.
- Primary tap targets are at least 44×44 px, including on iPhone SE. Pinch-zoom is allowed; `touch-action: manipulation` limits accidental double-tap zoom.
- Visible `:focus-visible` rings and `prefers-reduced-motion` support.
- The coach banner no longer hides the round's net result; both are shown together.
- Mid-hand shoe exhaustion no longer folds an old hole card into the new running count (see Table rules).
- Clear and Rebet persist the bet via `saveState()`.
- Service worker (`bj-trainer-v5`) caches only same-origin successful GET responses, precaches the new icons, deletes old caches, and reloads the page once when a new worker takes control.
