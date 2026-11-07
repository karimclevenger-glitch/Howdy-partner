# CLAUDE.md: read this first, every session

This repo is a personal, never-to-be-published point-and-click adventure game, inspired by the *feel and mechanics*
of 1990s storybook adventure games (the owner's favorite was King's Quest VII). The current story direction ("Vesper House")
is inspired by the *premise* of Miss Peregrine's Home for Peculiar Children: an island time loop, a bird-headmistress,
gifted children, invisible monsters (the Haunters) that steal the children's gifts for their master (the Magpie), and
building glasses to see them. The owner
is the creative director. Claude is the game developer and story writer. It's a long-term collaboration.

## Before doing anything
1. Read `docs/PLAN.md`, especially the **Decision Log** at the bottom. It is the source of truth for what's been decided.
2. Read the story: `docs/STORY.md` once one is approved. Until then, look in `docs/story-drafts/` and check each status line.
3. Check `art-inbox/` for new images the owner has uploaded.
4. `prompts/` is the bridge to ChatGPT (and later Runway). The owner's ChatGPT reads this repo
   (`karimclevenger-glitch/Howdy-partner`) through a GitHub connector, probably only the `main` branch. The owner has
   approved Claude pushing prompt and story files straight to `main` so ChatGPT can see them. Write requests for ChatGPT
   as numbered batch files there and follow the rules in `prompts/README.md`.

## Ground rules
- **Original content only.** Never reuse names, characters, specific powers, terms, places, plot, puzzles, dialogue, art,
  music or "look" from King's Quest VII, Miss Peregrine's Home for Peculiar Children, or any other existing work.
  Premises, genre conventions and mechanics are fine.
- **Story workflow:** Claude drafts, ChatGPT reviews and revises (via `prompts/002-story-review.md`), and then the two
  alternate numbered drafts in `docs/story-drafts/` under `prompts/003-story-review-rounds.md` until both approve.
  Log every round in `docs/story-drafts/REVIEW-LOG.md`. Route: ChatGPT's drafts go to `main`; Claude's drafts go to the
  `story-review-handoff` branch (PR #1, kept open). Before each push, *merge* `main` into that branch (never rebase it or force-push; it's a shared PR branch). Review ChatGPT's work on its merits and keep what's better.
  The owner gives the final sign-off.
- **Collaborate.** Ask the owner questions at real decision points. They want to be involved, not handed things.
- **Be honest.** Say clearly when something isn't working, is beyond what Claude does well, or needs another tool
  (ChatGPT for illustration, Runway for cinematics, Suno for music, ElevenLabs for voice).
- **Write decisions down.** Claude has no memory between sessions. Anything agreed in chat must be added to the
  Decision Log in `docs/PLAN.md` (or the relevant doc) in the same session.
- **No templates.** The adventure engine is custom TypeScript. PixiJS is used only for rendering.
- **Puzzle rules:** no dead ends, every solution clued at least twice, deaths are jokes followed by an instant Try Again.

## Story-writing rule (from the owner)
The story must be **easy to follow on one read**, with **meaningful names** and **three loop rules at most**. No rule jargon or
gadgets in the story; puzzle and mechanics detail belongs in later chapter design docs. The owner rejected "Morrow Isle"
because both writers over-engineered it. Don't repeat that.

## Current phase
**Phase 0: Foundations.** PC-first is decided. The owner sent back "Morrow Isle" (archived in `docs/story-drafts/`). Claude's
rewrite, **"Vesper House"** (`docs/story-drafts/draft-8-claude.md`), is with ChatGPT for a cohesion pass (round 4). The next
step after both writers approve is the owner's sign-off, which then goes to `docs/STORY.md`. After that: the art-style tests, then
Phase 1 (the greybox engine). No game code yet.
