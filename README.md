# DomiGo — 4th Grade Vocab Trainer

EFL vocabulary trainer for 4th-grade (4B) students at Gymnasium der Dominikanerinnen, based on **MORE! 4** (CEFR **A2+/B1**).

**Live:** https://veho-domi.github.io/4th-grade-vocab-trainer/

## What it does
Practice modes (Sprint, Speed, Multiple Choice, Flashcards, Full Run) and arcade mini-games (Memory Match, Word Hunt, Spelling Bee, Group Sort, Matching Pairs, Anagram). Grammar arcade with chat-sim campaign renderer. Battle Arena and Class Quiz support live multiplayer. Word Hunt is the most heavily curated of the four trainers (semantic-class discipline, U1–U13 rebuilt April 2026).

Story Mode campaign UI exists in the codebase but is hidden ("Coming Soon") — see CLAUDE.md for the path to enable it later.

## Tech
Single-file vanilla HTML/JS app (`index.html`, ~13K lines). Firebase (`veho-vocab` project) for student data. GitHub Pages for deployment. No build step.

## Workspace
Part of the DomiGo workspace. See [`../DOMIGO.md`](../DOMIGO.md) for the full inventory and workflow rules. See [`CLAUDE.md`](CLAUDE.md) for internal architecture and conventions, and [`CHANGELOG.md`](CHANGELOG.md) for release history.
