# Blackjack & Card Counting Trainer Pro

A self-contained, mobile-first Progressive Web App (PWA) for learning Basic Strategy, Hi-Lo card counting, Illustrious 18 & Fab 4 deviations, and optimal bet sizing across 1, 2 (Double Deck), 4, 6, and 8-deck shoes.

## Features
- **Table Play**: Full Blackjack with CSPRNG Fisher-Yates shuffling, burn card, deck-accurate penetration, exact $0.50 payouts, Insurance / Even Money, Late Surrender, live Count HUD, and Strategy/Deviation Coach.
- **Speed Count Drill**: 52-card Hi-Lo flashcard drill (1, 2, or 3 cards at a time; manual or auto-deal).
- **Strategy & Deviations Drill**: Rapid-fire Basic Strategy and Illustrious 18 / Fab 4 trainer.
- **Charts & Counting Guide**: Dynamic deck-accurate strategy cards (2D, 6D, 8D) and full Hi-Lo / Kelly / Wonging guide.
- **Offline Ready**: Installable via **Add to Home Screen** on iOS and Android.

## Table rules (implicit)
- American peek for dealer blackjack (Ace or 10-up). Insurance / Even Money are offered only when the dealer shows an Ace.
- Natural blackjack pays **3:2** (no 6:5 option).
- Late surrender, when enabled, is on the first two cards of a single unsplit hand.
- Split aces receive one card each and cannot be hit, doubled, or resplit (no RSA).
- A two-card 21 after a split is paid as a regular win, not a blackjack.
- If the cut-card shoe is exhausted mid-hand (rare at these penetrations), a **new shoe is shuffled to finish dealing**. The running count resets for the fresh shoe; cards already on the table, including a hidden hole card from the previous shoe, are not carried into the new count. The new shoe then continues for later hands.

## Changelog

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
