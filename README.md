# Mix & Spell: Colour Word Puzzle

A single-file HTML5 puzzle game built for YouTube Playables.

- **Developer account for Playables (user's explicit choice):** `subodhsinghlive@gmail.com`
  - Do NOT use `subodhkumarvermakv@gmail.com` (previous Playables choice, switched 12 Nov 2026).
  - Do NOT use `hello@getcerttracker.com`.
  - No sign-in was performed while building this game. Nothing was submitted anywhere.
- **Audience:** Ages **13+ only**, general audience, English (US tier-1: US / UK / Canada / Australia). **NOT made for kids.** No Aarav/Mia child characters, no kids branding.
- **Version:** **v2** (2026-11-12). Previous version: v1, 34,085 bytes, 304 tests, 0 failed.
- **File:** `index.html` — **60,940 bytes (~59.5 KB)**, self-contained. No external libraries, images, fonts, or audio files. The only external URL in the file is the official Playables SDK script tag.

## How to play

1. **Step 1 — Mix:** A target colour is shown. Tap two colours from the palette to mix it.
   - blue + yellow = green · red + blue = purple · red + yellow = orange
   - White lightens a colour, black darkens it.
   - A wrong mix costs 3 seconds in Levels 1–5 (5 seconds after that). A correct mix earns 5 coins.
2. **Step 2 — Spell:** Tap the scrambled letters in order to spell the English word for the colour/object you just mixed (e.g. GREEN, GRAPE, TIGER, OCEAN).
3. Beat the timer. You have **3 lives**. A wrong word resets the letters (no life lost); running out of time loses a life.
4. **Score:** 100 points per level + 5 per second left + 20 per streak level. Coins: +10 per level, +5 per correct mix.
5. **Hint:** 10 coins reveals the next letter (refused with a message if you have fewer than 10 coins — coins never go negative). **Shuffle** re-scrambles the unused letters. **Undo** frees the last letter.
6. **Daily Challenge:** 3 levels, +50 coins on completion. Daily streak counts consecutive days played.
7. **Endless mode:** after Level 50 the generator keeps producing new levels. Difficulty ramps gently — the timer is 60s at Level 1 and falls slowly to a 20s floor, and the word/target pool widens.
8. **Modes (v2):** **Classic** (Mix + Spell, above) and **60-Second Blitz** — colour-mix only, one tap per mix, as many mixes as possible in 60 seconds, combo multiplier (score = 10 × combo). Instant restart.
9. **Progression (v2):** achievements (First Mix, 5-Streak, 10 Levels, Blitz 20, Daily 3-Day), a daily mission on the menu (e.g. "Mix 5 greens today", +30 coins), a Day 1–7 daily reward calendar (10/20/30/40/50/75/100 coins), unlockable colour themes (Sunset 100, Ocean 200, Forest 300 coins — no purchases), and your personal best on the menu.
10. **Onboarding (v2):** a big "▶ TAP TO PLAY" button, a 3-step animated mini-tutorial (Mix → Spell → Score, under 20 seconds, auto-advances, skippable), and tutorial-easy Levels 1–3 (60s timer, only 3 colours, short words, practice hints). First coins land in the first 10 seconds of play.


## Design System v2 (world-class, CSS-only, single file)

- **Base theme — Royal Indigo:** background gradient `#0F172A → #1E1B4B → #312E81`; glassmorphism cards (rgba white 8%, blur 12px, 1px light border, 20px radius, soft shadow); text `#F8FAFC`, muted `#CBD5E1` (WCAG AA — never light grey on dark).
- **Primary:** Indigo `#6366F1` → Violet `#8B5CF6` gradient on buttons/accents. **Gold `#F59E0B / #FBBF24` only** for coins, rewards, streaks, achievements. Success `#10B981`, Danger `#EF4444`, Warning `#F59E0B`.
- **Typography:** system font stack only — `-apple-system, "Segoe UI", Roboto, Helvetica, Arial` (no external fonts, Playables rule). Title 800 / 32px / −0.5px letter-spacing, gradient text. Section headings 700 / 20px. Body 500 / 16px. Buttons 700 / 16px, normal case.
- **Spacing:** 8pt grid (8/16/24px); cards padding 20px; buttons min-height 52px; tap targets ≥48px; radius 16px cards / 999px pill buttons / 12px chips.
- **Micro-interactions (CSS only):** button press scale 0.97, hover lift, correct mix = green glow + pop + "+100" popup, wrong mix = gentle shake + red tint, streak = flame glow, level complete = confetti burst (CSS/canvas-drawn), timer bar green → amber → red, level progress bar (0% mix → 50% spell → 100% complete).
- **Game colours — colour-blind safe:** every colour has a name label AND a distinct shape glyph (never colour alone). Red `#EF4444` ●, Blue `#3B82F6` ■, Yellow `#FACC15` ▲, Green `#22C55E` ◆, Purple `#A855F7` ★, Orange `#F97316` ⬢, Pink `#EC4899` ♥, Teal `#14B8A6` ✚, Brown `#92400E` ♠, Black `#1F2937` ⬤, White `#F8FAFC` ○, Grey `#6B7280` ▓ (plus Sky `#38BDF8` ☁, Cream `#FEF08A` ◐, Maroon `#9F1239` ♦, Navy `#1E3A8A` ▬, Olive `#65A30D` ♣). Light swatches (white, yellow, cream) use dark `#1F2937` labels so the text stays readable.
- **Unlockable themes (coins only, NO purchases)** — each changes the FULL palette, not just the background: (1) Default Royal Indigo, (2) Sunset — bg `#1C0A2E → #7C2D12`, primary `#F97316 → #EC4899`, (3) Ocean — bg `#082F49 → #0E7490`, primary `#06B6D4 → #3B82F6`, (4) Forest — bg `#052E16 → #14532D`, primary `#22C55E → #14B8A6`. Theme switch applies instantly, saves via the SDK, and persists across reload.
- **One style on every screen:** menu, play, pause, level-complete, game-over — same header, same buttons, same spacing. Menu shows the game name in big gradient text with best score / coins / streak chips.
- **Design test results:** every theme × every screen checked at 320/390/800/1280/1920px in headless Chrome (7 screenshots viewed, 0 console errors after the boot fix — see `TEST-REPORT.md` §13). One cosmetic note: the longest palette label ("▲ 3 Yellow") wraps to a second line at 390px; the text stays fully visible, nothing is cut.

## Controls

- **Touch / mouse:** tap colours and letters.
- **Keyboard:** `1–5` pick a palette colour · letter keys type the word · `Backspace` undo letter · `Esc` pause.
- **Pause:** Pause button, `Esc`, switching tabs, or the platform's pause signal all pause the game and stop the timer.
- **Sound:** WebAudio oscillator beeps only; a Sound On/Off button, plus the platform mute signal, silences them.

## Monetization hooks (stubbed — no real ads in this file)

- **Interstitial:** offered only on the level-complete screen, after every 3 levels, and only if at least 90 seconds have passed since the last one. Never mid-gameplay.
- **Rewarded:** on Game Over, "Continue: +1 life (ad)" asks the platform for a rewarded ad. The life is granted ONLY if the ad actually played (or, in a normal browser with no platform, via the local stub so the button stays testable). If the ad is declined or fails, no life is given and the game stays on Game Over with an explanation.
- **Pre-roll:** YouTube's own — nothing for the game to do.
- No in-app purchases, no login, no external links, no sharing prompts, no quit button.

## How to test locally

1. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge) — desktop or phone. No server needed; double-click works.
2. Or serve it: `python3 -m http.server 8000` from this folder, then open `http://localhost:8000/index.html`.
3. Play at least Levels 1–10 (see `TEST-REPORT.md` for the automated playthrough).
4. Resize the window / rotate the phone: the layout is responsive for portrait, landscape, 1:1, 16:9 and 9:16.
5. Check the browser console: there should be no errors and no network requests except the SDK script (which is a no-op locally if it fails to load — the built-in stub takes over).

## What is NOT done yet (needs the user, not this build)

- **Playables interest form + Developer Portal approval.** Access is invitation-only and early-access; this build does not submit anything and cannot bypass that gate.
- **Real certification** in the Playables Developer Portal (test suite on desktop web, mobile web, Android, iOS) and **real ad testing** — both need portal access.
- **Thumbnails / store metadata** for the portal listing — see `COMPLIANCE-CHECKLIST.md` for what to prepare.

## Files in this folder

| File | What it is |
|---|---|
| `index.html` | The complete game |
| `README.md` | This file |
| `COMPLIANCE-CHECKLIST.md` | Every Playables rule, with PASS + evidence |
| `TEST-REPORT.md` | Self-review: automated tests + playthrough + bugs found/fixed |
