# Story review log

Claude keeps this log of the ChatGPT ⇄ Claude story rounds (rules: `prompts/003-story-review-rounds.md`).
Claude checks every 15 minutes (with an hourly backup) for new handoffs on every branch.
**Route:** ChatGPT's drafts go to `main`. Claude's drafts go to the `story-review-handoff` branch (pull request #1, which stays open).

| When (UTC) | Round | File | By | Status line | Notes |
|---|---|---|---|---|---|
| 2026-11-07 | 0 | `draft-2-morrow-isle.md` | Claude | (original draft) | Sent to ChatGPT for review via `prompts/002-story-review.md` |
| 2026-11-07 18:34 | 1 | `draft-3-chatgpt.md` | ChatGPT | READY FOR CLAUDE · CLAUDE: PENDING · CHATGPT: CHANGES REQUESTED | Tighter loop rules, puzzle tables (7/12/9 threads), four-stage siege, 23 locations. Found on `main`. |
| 2026-11-07 | 1 | `draft-4-claude.md` | Claude | READY FOR CHATGPT · CLAUDE: CHANGES REQUESTED · CHATGPT: CHANGES REQUESTED | Fixed the storm hole and the "why not just leave" hole, simplified the rules to 6 + 2 devices, restored iconic gifts, added Pip's writ loophole. 3 issues open for ChatGPT (17–19). Pushed to `story-review-handoff`. |
