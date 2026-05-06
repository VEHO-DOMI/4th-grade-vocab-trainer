# CHANGELOG — 4th Grade Vocab Trainer

Reverse-chronological release history. Going forward, update on each substantive change. Earlier history (pre-2026-04-11) lives only in `git log`.

## 2026-05-06 — Activity Game mode
- New sibling app at `activity/` — teacher-orchestrated group game for 4B: **Draw It** ✏️ / **Show It** 🎭 / **Explain It** 💬, plus mix-mode with per-word category cue.
- Setup: ≥2 group names, time-per-round picker (30 / 60 / 90 s), 3/5/8/∞ rounds-per-group, multi-select modes (≥1 required), multi-select 13-unit grid with quick-chips (All / None / U1–4 / U5–7 / U8–10 / U11–13), live "words available" counter, optional time-bonus toggle.
- Group scoring with two-stage tie-break (correct-total then skip-total) and 🤝 Tie badge.
- 443 MORE 4 vocab entries categorized **from scratch** through an A2+ 13–14 yo lens — every word reviewed individually with a written justification (244 high-confidence calls, 199 medium-confidence). Distribution: 81 Draw / 117 Show / 245 Explain (Explain bias stronger than G3 because MORE 4 has heavier abstract content: politics, history, social issues, science). Tooling at `TOOLS/activity-audit-g4/`; per-word reasoning in `reports/g4-categorizations.csv`; review guide in `TEACHER_REVIEW.md`. The master `Full Vocabulary List MORE 4 Units 1-13.docx` was used for cross-reference (clean).
- Cross-grade consistency: words appearing in both G3 and G4 (`crawl`, `whisper`, `shocked`, `evacuate`, `celebrate`, `border`, `prefer`, `attend`, etc.) get identical categorizations.
- Sensitive content (`murder`, `execute`, `slavery`, `racism`, `addiction`, `eating disorder`, `depressed`) all sit in Explain — handled in words rather than mime/draw.
- Mobile-first dark theme with G4 purple brand accent. Rich SFX (coin-pickup correct, whoosh skip, klaxon buzzer, fanfare bonus, start chime, game-over chord). Big 84-px Correct + Skip; Undo demoted.
- Home-screen card "🎯 Activity Game" links to `activity/`. No login / Firebase / XP — pure classroom group game with `localStorage` history.

## 2026-05-01 — Phase 0 polish (cross-grade)
- Fix stray "60" timer always visible at top of practice modes (`speed-timer-wrap` now properly hidden when not in Speed Round).
- Fix XP-for-zero-correct exploit: ending a session with no correct answers now awards 0 XP instead of streak-bonus + perfect-round bonuses.
- Results page: friendly placeholder for sessions with no attempted words instead of blank `RESULTS` box.
- (Word Hunt: G4 already had a softened multi-mistake variant — no change needed.)
- Same fix-set applied across G1 (already shipped), G2, G3, G4.

## 2026-04-19 — Bugfix sweep
- Fix Spelling Bee auto-click XP exploit
- Fix results-page navigation

## 2026-04-18 — Word Hunt rebuild
- Word Hunt: rebuild U4–U13 with odd-one-out / semantic-class discipline
- Word Hunt v5: distractors from clearly different semantic classes
- Word Hunt v4: tighten category scopes and exclusion rules (U1–U3)
- Word Hunt v3 (EFL-style): distractors and sub-instruction line (U1–U3)
- Word Hunt: rebuild Units 2 and 3 from MORE! 4 vocab lists
- Word Hunt infrastructure: flexible round size, cleaner tile layout, U1 rebuilt
- Word Hunt: allow retry on wrong tap, show missed tiles in green
- Rebuild Word Hunt: 12-tile rounds with curated same-unit distractors
- Normalize practice-card subtitle to "Choose units and exercise type"
- Accept single-word corrections in error-correction word-selection mode

## 2026-04-14 — Vocab arcade (G4-tuned)
- Replace keyword-based vocab game categorizer with curated per-unit Memory Match / Word Hunt / Spelling Bee (all 13 units)
- New: Memory Match (12 pairs, phrase-aware, definition-aware matching), Word Hunt (B1 themes, 8 rounds), Spelling Bee
- Unified context/definition types with progressive 2-tier Hint button (XP penalty)

## 2026-04-13 — Grammar arcade additions
- Group Sort, Matching Pairs, Anagram added to grammar arcade
- Chat-sim campaign renderer
- Fix G4 save crash: remove call to undefined `addWeeklyGoalXP()`
- XP burst + combo tier-up animations across vocab modes
- Distractors added to 94 reclassified gap-fill items
- Fix: gap-fill items without distractors fall back to typed input
- Fix: `saveSessionResults` flashcard-status preservation scoping bug

## 2026-04-12 — Vocab audit + flashcards + level badge
- G4 vocab audit: add `col` field (odd-one-out + word partners) to all 443 items, fix 5 em-dashes
- Grammar audit: sync cumulative blocks, fix G4 overwrite bug, add missing M2/M3 to G4
- Matching parser supports dash-separated prompt format
- Tinder-style flashcard layout (multiple iterations)
- Flashcard tracking + dictionary integration
- Flashcard status persistence across page refreshes
- Mode switch button restored on home screen and added to profile card
- Level badge: bigger + shadow, fix stuck popup

## Earlier
Initial buildout, original Word Hunt with auto-categorizer, Word Partners (collocation MC), Class Quiz, prestige system, journey map. See `git log` for raw history.
