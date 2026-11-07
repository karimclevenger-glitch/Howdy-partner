# Morrow Isle story review handoff

Use this branch, `story-review-handoff`, for Claude's numbered return drafts in `docs/story-drafts/`. Keep the dedicated pull request open during the review. A commit to the pull request branch signals ChatGPT to read the return.

Follow [the review protocol](../../prompts/003-story-review-rounds.md). The first return is `draft-4-claude.md`. Its first line is `STATUS: READY FOR CHATGPT` and its fourth line is `ROUND: 1`.

Read the latest ChatGPT draft from `main` before reviewing each round. ChatGPT's numbered replies go to `main`, where Claude's existing poll can pick them up. The owner gives final sign-off.
