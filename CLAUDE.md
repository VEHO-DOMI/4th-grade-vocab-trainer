# CLAUDE.md — 4th Grade Vocab Trainer (G4)

Internal docs for Claude Code sessions and future maintainers. For users see [README.md](README.md). For workspace-wide rules see [`../DOMIGO.md`](../DOMIGO.md).

## Architecture

Single-file SPA. G4 has the most heavily curated Word Hunt content (semantic-class discipline, U1–U13 rebuilt April 2026). Story Mode UI scaffolding exists but the entry button is hidden ("Coming Soon").

- Total: ~13,017 lines
- `const vocabData = {` starts at line **2273**

## File layout

```
4th-grade-vocab-trainer/
├── index.html         ← entire app (HTML + inline CSS + inline JS + vocabData)
├── avatars/           ← 50 PNG avatars
├── activity/          ← Activity Game sibling app (Draw / Show / Explain)
│   ├── index.html     ← standalone group game; no login, no Firebase, no XP
│   └── data/
│       └── activity-words.js  ← auto-generated; rebuild via TOOLS/activity-audit-g4/
└── README.md, CLAUDE.md, CHANGELOG.md
```

No `campaign/` folder yet — campaign assets haven't been added because the Story Mode entry is hidden. Screens `campaign-map-screen`, `campaign-comic-screen`, `campaign-level-info-screen` exist in the markup. To enable Story Mode later: at line 1666, the `mode-campaign-card` button currently has `onclick="alert('Story Mode coming soon!')"` and `style="…opacity:0.5;display:none;"` — remove those guards and wire the proper handler.

## Modes shipped

**Practice modes:** Full, Sprint, Speed Round, Multiple Choice, Flashcards.

**Exercise types:** Context (easy/hard), Definition (easy/hard), Translation, Mix.

**Vocab arcade** (curated per-unit, A2+/B1):
- Memory Match (12 pairs, phrase-aware, definition-aware matching), Word Hunt (B1 themes, 8 rounds, semantic-class discipline), Spelling Bee
- Group Sort, Matching Pairs, Anagram

**Grammar arcade:** chat-sim campaign renderer, group-sort / matching-pairs / anagram task types.

**Live multiplayer:** Battle Arena, Class Quiz.

**Activity Game (sibling app at `activity/`):** teacher-orchestrated group game — Draw / Show / Explain (multi-select), 30/60/90 s rounds, 3/5/8/∞ rounds-per-group, multi-select 13-unit picker, group scoring with tie-break, optional time bonus. No login. Words come from `activity/data/activity-words.js` (single primary category per word, 443 entries categorized through an A2+ lens). Regenerate via `TOOLS/activity-audit-g4/build-activity-words.js` after editing `teacher-overrides.csv`.

**Disabled (scaffolded):** Story Mode (campaign-comic-screen, campaign-level-info-screen).

## Firebase

- Project: `veho-vocab`
- Realtime DB: `https://veho-vocab-default-rtdb.europe-west1.firebasedatabase.app`
- Firestore path: `classes/<CLASS_ID>/students/<slug>/`
- `let CLASS_ID = null;` — set per class during login.

## Deploy

Push to `main` → GitHub Pages → https://veho-domi.github.io/4th-grade-vocab-trainer/. No CI, no build step.

## Conventions (the things that have bitten us)

- **Language level A2+/B1 — the most advanced of the four.** Sentences can use present perfect, conditionals, passives, relative clauses where curriculum supports them. Definitions ~10–18 words.
- **Definitions must not leak the headword.**
- **Context sentences must be original** — never copy the textbook example.
- **German `g` field is verbatim from MORE! 4.**
- **`cf` field only when needed.**
- **Vary verb forms.**
- **Word Hunt distractor discipline (G4-specific).** Distractors must come from clearly different semantic classes (the Apr 18 v3-v5 rebuilds existed because earlier rounds had distractors that were too similar to the answer set). Maintain odd-one-out / semantic-class scope when adding new units.
- **G4 vocab `col` field.** All 443 items have a `col` field (odd-one-out + word partners) — preserve it on edits.
- **Single-file edits at scale.**
- **Always `git pull` before editing.**

## Vocabulary source

`Domi Gym 2025:26/4B (2025:26)/MORE 4 Materials & Resources/` — full vocab list .docx is in this folder. Extract verbatim, do not hallucinate.

## Known issues / TODOs

- Story Mode is scaffolded but disabled. Re-enabling requires removing the alert + hidden styles, providing campaign content, and adding the campaign/ image folder.
- Word Hunt was rebuilt extensively April 18; further unit additions should follow the same odd-one-out / semantic-class pattern.
- G4 had a save-crash bug with `addWeeklyGoalXP()` (fixed 2026-04-13) — be careful adding new XP-related calls without defining the function.
- Long-term: fold into unified DomiGo app.
