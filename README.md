# Blackjack & Card Counting Trainer Pro

A self-contained, mobile-first Progressive Web App (PWA) for learning Basic Strategy, Hi-Lo card counting, Illustrious 18 & Fab 4 deviations, and optimal bet sizing across 1, 2 (Double Deck), 4, 6, and 8-deck shoes.

## Features
- **Table Play**: Full Blackjack with CSPRNG Fisher-Yates shuffling, a face-down burn card (uncounted), deck-accurate penetration, exact $0.50 payouts, Insurance / Even Money, Late Surrender, live Count HUD, and Strategy/Deviation Coach. Cards are dealt one at a time in casino order (first base to third base, then the dealer, hole card down). You can sit first base through third base when other seats are on. Busted hands are swept immediately; the round is swept at the end unless Last-round review is on.
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
- Split aces receive one card each by default (Rules toggle, casino standard) and cannot be resplit (no RSA). Turn the rule off to hit or double split aces (DAS still applies). A 10 on a split ace is a regular 21, not a blackjack.
- A two-card 21 after a split is paid as a regular win, not a blackjack.
- If the cut-card shoe is exhausted mid-hand (rare at these penetrations), a **new shoe is shuffled to finish dealing**. The running count resets for the fresh shoe; cards already on the table, including a hidden hole card from the previous shoe, are not carried into the new count. The new shoe then continues for later hands.

## Feature guide (v14)

v14.0 adds realistic Table Play dealing and seat choice on top of every v13.3 feature. Cards appear in place at a per-page **Deal pace** (Instant / Fast / Normal / Slow; Normal by default; instant when the device requests reduced motion). Deal order is left to right, first base to third base, then the dealer, twice, with the hole card face down and uncounted until the dealer’s turn. Pick **Your seat** when other players are at the table; they act in seat order with basic strategy. Busts are swept at once, and the whole layout is swept at the end of the round so you have to count while the cards are visible. **Last-round review** (off by default) keeps the finished hands until the next Deal — the v13.3 linger. A hidden **#selftest** page runs shoe-composition, strategy, deal-order, burn, and hole-card checks for this build. Features 4–9 (mistake replay, progress charts, random TC quizzes, index prompts, distraction mode, and export/import) are not in 14.0 and will follow as v14.x. Feature 5 from the original roadmap (RSA / 6:5 / early surrender) is still not in the app.


v13.3 fixes Jerry's v13.2 QA bugs: per-page Settings now hide options that don't belong on that page; Speed Count keeps accumulated run time across pauses and at shoe end (and only then records Best); Apply to all no longer rebuilds the Table shoe unless Play's decks actually change; Strategy and Risk settings show their own values.

## Feature guide (v13.2)

Speed Count keeps a large full-width **Deal** button on the top row. The bottom row is three equal buttons: **New Shoe**, **Start**, and **Check Count**. New Shoe reshuffles and resets the count, cards seen, and timer to 0, then waits at Ready — the timer does not start until you press Start. Deal, felt tap, and Space do not start a run. Changing Speed settings mid-run returns to Ready.

## Feature guide (v13.1)

Speed Count uses a large full-width **Deal** button on the top row (it also starts a run if one has not begun). The bottom row is **New Shoe** and **Check Count**. Deal is disabled while Auto is running and after the shoe ends. Tap the felt or press Space to deal in Manual mode.

## Feature guide (v13)

v13 gives every mode its own Settings menu (the header gear opens the current page). Table Play, Speed Count, Strategy Drill, Charts, and Risk Tools keep their own decks and rules; App settings only hide modes and reset data. **Apply to all pages** copies shared options such as decks or dealer rules to the pages that have them. Speed Count has a cleaner layout, a **New Shoe** button that reshuffles and restarts immediately, and optional 1/2/4/6/8-deck shoes (a full shoe still ends at RC 0).

## Feature guide (v12)

v12 keeps the v11 history and split-aces features and fixes four QA items: the header mode label fits on a 320 px phone (it shortens to **Hand History** under 360 px), the result banner no longer tucks under dealer cards on a 360×780 split, `BJ_QA.shoeComposition()` still reports a full pack after a reload or a v11 upgrade, and a history row only shows RC/TC if the count HUD was on when that hand was bet.

## Feature guide (v11)

v11 adds **Hand History (this shoe)** — a review of every completed round in the current shoe (bet, cards, actions vs basic/deviations, insurance, net, and the count at bet time). The list resets on a new shuffle and survives a reload in the same shoe. A Rules toggle, **Split aces receive one card only**, is on by default; turn it off to play split aces like other split hands. Settings rows no longer let a dropdown paint over its label (v10-1).

## Feature guide (v10)

v10 fixes the Betting Strategy dropdown so every Rules / Settings label is fully readable (the auto spread reads **Auto by deck (1–8 / 1–12)**). A new Settings → Features toggle, **Show card totals** (on by default), hides the total pills on the dealer, your hand, split hands, and other seats so you can practice adding the cards. Busts and blackjacks are still announced, the coach will not name the total, and you can tap a hidden total to peek for the rest of the round.

## Feature guide (v9)

v9 keeps the live shoe and discard bars and fixes mid-hand UX: the deck-estimate prompt now fires after every N completed hands (5, 10, or 15), not N+1. Grade bets stays visible next to the recommended bet after Deal. Tight iPhone SE (320×568) portrait keeps the result banner readable and every split card scrollable. Overflowing split hands show a fade and chevron when more cards sit off-screen. Settings dropdowns and short-landscape hand titles stay fully readable. How It Works lists every Settings → Features toggle, including Grade bets, quizzes, timed decisions, other seats, and heat hints.

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

### v14.0.2
- The bust card is drawn on the felt and stays visible for a countable beat (scaled with deal pace; about two seconds at Normal) before the hand is swept, for you and for the other seats. It is no longer counted and whisked away before you can see it.
- The dealer’s hole card and each dealer hit appear one at a time at the deal pace. The end-of-round sweep waits that same countable beat (1.5–2.5 s at Normal; Instant stays fast but still shows every card).
- Cards already on the table are not recreated on later deal steps, so they no longer flicker or replay a fade/slide. The 0.14 s slide-in animation is gone: cards simply appear in place.
- After a cut-card reshuffle, the “Cut card reached — fresh shoe shuffled (1 burned, unseen). RC = 0” notice stays on Your turn (and in a persistent line under the feedback bar) so Instant pace no longer hides it (Jerry N2).
- The hidden `#selftest` page is a separate full view: it no longer shares the column with Table Play or squashes the felt on desktop (Jerry N3).
- Speed Count’s Deck Estimate Drill still follows only Speed’s toggle (Jerry N1). Cache `bj-trainer-v14-0-2`.

### v14.0.1
- Speed Count's Deck Estimate Drill button follows only Speed's own toggle, not Table Play's (Jerry N1). Cache `bj-trainer-v14-0-1`.

### v14
- Table Play deals one card at a time in casino order (first base → third base → dealer, two rounds). The hole card stays face down and uncounted until it is revealed. The burn card after a shuffle stays unseen and is never counted.
- **Deal pace** (Table Play Settings): Instant, Fast, Normal (default), or Slow. Cards simply appear; there is no flip, slide, or 3D motion.
- **Your seat** (first base through third base) when other seats are on. Other players act in that order with basic strategy, before and/or after you.
- Busted hands are swept immediately. At the end of the round every hand is swept unless **Last-round review** is on (that restores the v13.3 “cards stay until Deal” behavior).
- Hidden `#selftest` page (not in the mode menu) runs composition, strategy, deal-order, burn, and hole-card checks.
- All v13.3 modes, drills, per-page settings, Apply to all, and the Speed Count Ready / Start / Deal flow are unchanged. Service worker cache bumped to `bj-trainer-v14`.

### v13.3
- Per-page Settings only show the current page's options (`[hidden]` is no longer overridden by `display: grid`). A control that does not belong on the page cannot write Table Play values.
- Speed Count accumulates active time across mid-shoe Check pauses, tab switches, and shoe end, so the result and Best use the real run time (not 0.0s or a pre-pause fragment).
- Apply to all rebuilds the Table Play shoe only when Play's deck count actually changes; otherwise history and the current shoe stay put. A Speed run returns to Ready only if Speed's values actually changed mid-run.
- Strategy and Risk settings show their own stored values when reopened. Speed's Deck Estimate Drill uses Speed's deck count. The header mode stays in sync after a Firefox reload. The History label stays complete at 360 px (compact "Hand History" when the full label would clip).
- Service worker cache bumped to `bj-trainer-v13-3`.

### v13.2
- Speed Count: **New Shoe** and **Start** are separate. New Shoe goes to an idle Ready state (timer at 0, no card dealt). **Start** begins the timer and deals the first card(s). Deal stays the large top button but is disabled until Start (hint: "Press Start when ready"), during Auto, after the shoe ends, and while the count prompt is open. After a mid-shoe Check, Deal continues the same shoe without resetting the timer to 0. Changing Speed settings mid-run returns to Ready.
- Service worker cache bumped to `bj-trainer-v13-2`.

### v13.1
- Speed Count buttons: one large full-width **Deal** on the top row (deals the next card(s) and starts a run if needed). Bottom row is two equal buttons, **New Shoe** and **Check Count**. The extra Start / Restart control is gone. Deal is disabled during Auto deal and after the last card; felt tap and Space still deal in Manual mode.
- Service worker cache bumped to `bj-trainer-v13-1`.

### v13
- Per-page settings: the header gear opens options for the current mode only. Existing universal settings are copied into each page on upgrade so nothing is lost. **Apply to all pages** copies that page's shared settings (decks, dealer rules, HUD, tags, and so on) to every other page that has them, with a short confirmation.
- A small **App settings** section is for mode visibility and data reset only (this build has no theme control).
- Speed Count: cleaner phone and desktop layout, a **New Shoe** reset that reshuffles and restarts immediately (count, cards seen, and timer), and a per-page shoe of 1, 2, 4, 6, or 8 decks. Check still works mid-shoe; a full shoe still finishes at RC 0.
- Service worker cache bumped to `bj-trainer-v13`.

### v12
- v11-1: the header mode menu no longer clips **Hand History (this shoe)** on a 320 px phone; under 360 px the label shortens to **Hand History**. Every header option is checked at 320 and 360.
- v11-2: after a split on a 360×780 phone, dealer cards no longer sit under the result banner (the felt scrolls instead of shrinking the cards under the history-link height).
- v11-3: the dealt cards and burn card are saved with the shoe, and a v11 snapshot that lacked them is reconstructed, so `BJ_QA.shoeComposition()` stays `ok: true` after a reload or upgrade.
- v11-4: a history row shows "At bet: RC/TC" only if the count HUD was on when that hand was bet — turning the HUD on later does not rewrite older rows.
- Service worker cache bumped to `bj-trainer-v12`.

### v11
- **Hand History (this shoe)** in the mode menu, plus a quick link under the table. Each entry has round #, time, bet and units, player hands (splits/doubles), dealer cards, totals, actions vs the correct basic or deviation play (mistakes marked), insurance, outcome and net, and RC/TC/decks at bet time when those tools were on. Completes only when a round ends (a mid-round reload does not write a partial hand). The list is this shoe only and clears on a shuffle; it is saved so a reload in the same shoe keeps it. Filter to mistakes, or Clear with a confirm.
- **Split aces receive one card only** (Rules, on by default). On: each split ace gets one card and stands — no hit, double, or resplit. A 10 on a split ace is 21, not blackjack. Off: split aces play normally (hit / DAS), still with no RSA. Table play, other seats, the coach, charts callout, and the soak sim all follow the toggle.
- v10-1: in Rules / Settings / Features, a wrapping label no longer sits under its `<select>` or number field — the control starts on the line below at full width.
- Service worker cache bumped to `bj-trainer-v11`.

### v10
- Rules / Settings `<select>` labels are fully visible on every viewport. The Betting Strategy option is now **Auto by deck (1–8 / 1–12)** and the dropdown wraps to a full row when space is tight, so text is no longer clipped before the arrow.
- **Show card totals** (Settings → Features, on by default) can be turned off to practice mental math. Dealer, player, split, and other-seat totals hide; busts and blackjacks are still announced; the coach and Strategy Drill do not name the total. Tap a hidden total to reveal it for the rest of the round. The choice persists.
- Service worker cache bumped to `bj-trainer-v10`.

### v9
- Deck-estimate auto-prompt now fires after N completed hands (every 5 / 10 / 15), not N+1.
- Grade bets remains on screen next to the recommended bet after Deal, and clears when you change the wager.
- iPhone SE 320×568 portrait: the result banner stays readable after a split, and every split card can be scrolled into view without dealer cards covering it.
- Overflowing split hands show a fade and chevron cue when more cards sit off the right (or left) edge.
- Settings selects fit their labels on iPhone and iPad; short-landscape hand titles and results (H1, BUST, WIN) are no longer mid-word truncated.
- How It Works → What each toggle does now names Grade bets, count quizzes, timed decisions, other seats, and heat hints, matching Settings → Features.
- Service worker cache bumped to `bj-trainer-v9`.

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
