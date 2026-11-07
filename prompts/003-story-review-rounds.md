# Batch 003: Story review rounds (ChatGPT ⇄ Claude, until both sign off)

**For ChatGPT:** read [`README.md`](README.md) and [`002-story-review.md`](002-story-review.md) first. This file explains how
you and Claude pass the story back and forth until **both of you approve it**. The owner then makes the final call.

## The goal of every round
Make the story **robust**:
- **No story holes**, meaning nothing contradicts itself or the loop's rules.
- **Full of adventure,** with memorable set-pieces and places worth exploring.
- **Full of good puzzles** that are fair, varied, clued at least twice, and can't leave the player stuck.

Approving means *"I'd put my name on this story."* It does not mean "good enough." Don't approve while you have open issues.

## How a handoff works
Every handoff is a **new file** in `docs/story-drafts/`, numbered in order:

| Round | File | Written by |
|---|---|---|
| 1 | `draft-3-chatgpt.md` | ChatGPT (from batch 002) |
| 1 | `draft-4-claude.md` | Claude |
| 2 | `draft-5-chatgpt.md` | ChatGPT |
| 2 | `draft-6-claude.md` | Claude |
| … | and so on | |

**The first five lines of every handoff file must follow this format.** Claude checks for it automatically. Line 5 is a
plain-English note to the other writer, saying it's their turn and what to do:

When Claude hands off to ChatGPT:
```
STATUS: READY FOR CHATGPT
CLAUDE: CHANGES REQUESTED
CHATGPT: CHANGES REQUESTED
ROUND: 1
NOTE TO CHATGPT: Your turn to review. Read this whole file, fix or answer every OPEN issue in "Review notes", then hand back draft-5-chatgpt.md following prompts/003-story-review-rounds.md.
```

When ChatGPT hands off to Claude:
```
STATUS: READY FOR CLAUDE
CLAUDE: CHANGES REQUESTED
CHATGPT: APPROVED
ROUND: 2
NOTE TO CLAUDE: Your turn to review. I resolved issues 1–6 and left 7 open (see Disagreements).
```

- Line 1 is `STATUS: READY FOR CLAUDE` when ChatGPT hands off, `STATUS: READY FOR CHATGPT` when Claude hands off, and
  `STATUS: BOTH APPROVED` when the story is done.
- Lines 2–3 hold each writer's latest verdict: `APPROVED`, `CHANGES REQUESTED`, or `PENDING` (not reviewed yet).
- You only change **your own** verdict line. Copy the other writer's line exactly as they left it, unless the other
  writer's verdict was APPROVED and you've since made significant changes. In that case, reset it to `PENDING`.

After those five lines, every handoff file has:
1. **`## Review notes`**: a numbered list of issues, each marked **OPEN** or **RESOLVED**, with who raised it. Keep
   earlier issues in the list and update their status, so nothing gets lost between rounds.
2. **`## Changes in this version`**: what you changed and why, one line each.
3. **`## Disagreements for the owner`**: anything you and the other writer can't agree on after two rounds. Describe both
   sides fairly and let the owner decide.
4. **The complete story**, in the same section structure as before.

## Where the file goes
- **If you can write to the repo,** save it at `docs/story-drafts/<file name>` on the `main` branch (or on any branch or pull
  request). Claude checks every branch.
- **If you can't,** give the owner the file to download. They'll upload it to `docs/story-drafts/` on GitHub (Add file → Upload files).

## The review checklist (both writers use it)

**Story holes**
- Are the loop's rules consistent everywhere: what resets, who remembers, what the player keeps, what happens to things the
  player takes, and why there's no duplicate of an item after a reset?
- Does every character have a clear motive? Why does the player stay? Why the letters? Why do the monsters come *now*? What are
  the villain's rules and limits (for example, why doesn't he simply walk in on day one)?
- Does the "you wrote the letters" twist hold together?
- Does every child have an introduction, a problem, a solution, and a payoff in the finale, each with a distinct voice?
- Does every preparation item have a use in the finale? Is there more than one way to win? Are the ending conditions clear?

**Adventure and puzzles**
- Each day should have **at least two memorable set-pieces** (for example, a sea cave at low tide, or climbing the lighthouse
  at a certain minute).
- Puzzle count targets: **Day 1 about 6–8, Day 2 about 10–14, Day 3 about 8–10**, plus the siege.
- Use a **variety of puzzle types**: inventory combinations, trades and dialogue, timing (the islanders' routines),
  loop exploits (knowledge or items carried across resets), the children's gifts, a few self-contained mechanical or logic puzzles,
  and secrets hidden in items you inspect.
- Every puzzle needs **two in-world clues**, and none can rely on guessing the designer's mind.
- Keep **several puzzle threads open at once**, so being stuck on one never means being stuck on everything.
- **No permanent dead ends.** Only the siege can be lost, and losing it rewinds.
- Include **eerie-funny deaths** with Try Again, about 4–6 per day.
- Include **optional content** worth finding (side quests and secrets) that pays off in the finale.

**Guardrails**
- **Originality:** nothing from *Miss Peregrine's Home for Peculiar Children* or *King's Quest*, including characters, names,
  specific powers, terms or plot beats.
- **Scope:** one house and one island, about 20–25 locations at most.
- **Tone:** PG, spooky rather than gory.

## When it's finished
When a handoff has **both** `CLAUDE: APPROVED` and `CHATGPT: APPROVED`, its first line becomes `STATUS: BOTH APPROVED`. Claude
then copies it to `docs/STORY.md` for the **owner's final sign-off**. The owner always has the last word.

If you've been through **four rounds each** without agreeing, stop and hand the owner the list of disagreements instead of
going in circles.
