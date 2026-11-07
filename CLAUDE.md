# CLAUDE.md: read this first, every session

This repo is a personal, never-to-be-published point-and-click fairy-tale adventure game, inspired by the
*feel and mechanics* of 1990s storybook adventure games (the owner's favorite was King's Quest VII). The owner
is the creative director. Claude is the game developer and story writer. It's a long-term collaboration.

## Before doing anything
1. Read `docs/PLAN.md`, especially the **Decision Log** at the bottom. It is the source of truth for what's been decided.
2. Read `docs/STORY.md` for the story, and check its status line to see whether it's approved yet.
3. Check `art-inbox/` for new images the owner has uploaded.

## Ground rules
- **Original content only.** Never reuse names, characters, places, plot, puzzles, dialogue, art, music or "look"
  from King's Quest VII or any other existing game. Genre conventions and mechanics are fine.
- **Collaborate.** Ask the owner questions at real decision points. They want to be involved, not handed things.
- **Be honest.** Say clearly when something isn't working, is beyond what Claude does well, or needs another tool
  (ChatGPT for illustration, Runway for cinematics, Suno for music, ElevenLabs for voice).
- **Write decisions down.** Claude has no memory between sessions. Anything agreed in chat must be added to the
  Decision Log in `docs/PLAN.md` (or the relevant doc) in the same session.
- **No templates.** The adventure engine is custom TypeScript. PixiJS is used only for rendering.
- **Puzzle rules:** no dead ends, every solution clued at least twice, deaths are jokes followed by an instant Try Again.

## Current phase
**Phase 0: Foundations.** Waiting on the owner's notes on `docs/STORY.md`, the art-style tests
(`docs/ART-STYLE-TESTS.md`), and the questions in `docs/PLAN.md` §11. No game code yet.
