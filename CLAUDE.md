# CLAUDE.md: read this first, every session

This repo is a personal, never-to-be-published point-and-click adventure game, inspired by the *feel and mechanics*
of 1990s storybook adventure games (the owner's favorite was King's Quest VII). The current story direction is
inspired by the *premise* of Miss Peregrine's Home for Peculiar Children: an island time loop, a bird-headmistress,
unusual children, invisible monsters, and building glasses to see them. The owner
is the creative director. Claude is the game developer and story writer. It's a long-term collaboration.

## Before doing anything
1. Read `docs/PLAN.md`, especially the **Decision Log** at the bottom. It is the source of truth for what's been decided.
2. Read the story: `docs/STORY.md` once one is approved. Until then, look in `docs/story-drafts/` and check each status line.
3. Check `art-inbox/` for new images the owner has uploaded.
4. `prompts/` is the bridge to ChatGPT (and later Runway). The owner's ChatGPT reads this repo through a GitHub
   connector, probably only the `main` branch, so prompt files must be merged to `main` before ChatGPT can see them.
   Write requests for ChatGPT as numbered batch files there and follow the rules in `prompts/README.md`.

## Ground rules
- **Original content only.** Never reuse names, characters, specific powers, terms, places, plot, puzzles, dialogue, art,
  music or "look" from King's Quest VII, Miss Peregrine's Home for Peculiar Children, or any other existing work.
  Premises, genre conventions and mechanics are fine.
- **Story workflow:** Claude drafts, ChatGPT reviews and revises (via `prompts/002-story-review.md`), and then the two
  alternate numbered drafts in `docs/story-drafts/` under `prompts/003-story-review-rounds.md` until both approve.
  Log every round in `docs/story-drafts/REVIEW-LOG.md`. Review ChatGPT's work on its merits and keep what's better.
  The owner gives the final sign-off.
- **Collaborate.** Ask the owner questions at real decision points. They want to be involved, not handed things.
- **Be honest.** Say clearly when something isn't working, is beyond what Claude does well, or needs another tool
  (ChatGPT for illustration, Runway for cinematics, Suno for music, ElevenLabs for voice).
- **Write decisions down.** Claude has no memory between sessions. Anything agreed in chat must be added to the
  Decision Log in `docs/PLAN.md` (or the relevant doc) in the same session.
- **No templates.** The adventure engine is custom TypeScript. PixiJS is used only for rendering.
- **Puzzle rules:** no dead ends, every solution clued at least twice, deaths are jokes followed by an instant Try Again.

## Current phase
**Phase 0: Foundations.** PC-first is decided. Story Draft 1 was not approved. Draft 2 (the owner's Miss-Peregrine-inspired
concept, `docs/story-drafts/draft-2-morrow-isle.md`) is out for ChatGPT review. Waiting on the art-style tests (`prompts/001-art-style-tests.md`) and the open questions in
`docs/PLAN.md` §11. No game code yet.
