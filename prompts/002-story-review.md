# Batch 002: Story review (ChatGPT as story editor)

**For ChatGPT:** read [`README.md`](README.md) in this folder first. This time you're a **story editor and game writer**,
not an illustrator.

## What to read
The story draft is [`docs/story-drafts/draft-2-morrow-isle.md`](../docs/story-drafts/draft-2-morrow-isle.md).

For background, there's an earlier draft in the same folder (`draft-1-the-long-dusk.md`) that the owner **did not like**,
and the overall project plan is in [`docs/PLAN.md`](../docs/PLAN.md).

## Your job
Make this story **better as a video game**: more memorable characters, sharper humor and dread, stronger twists,
better puzzles, and a more satisfying finale. Be honest. If something is weak, generic or confusing, say so plainly.

## What must stay (the owner's own concept)
- A visitor reaches an island because of something they read, then enters a **one-day time loop**.
- A **headmistress who turns into a bird** and **resets the loop** to protect a house of **unusual children**.
- **Exploring the house, talking to everyone, and collecting and combining items** is the core of the game.
- **Invisible monsters.** The player **can't see them** and must **build special glasses** to do so.
- **Building weapons and preparing** for a final battle. **Preparation decides the outcome**, and an unprepared
  player **can lose** the final battle.
- The feel of a classic point-and-click adventure: inventory puzzles, eccentric characters, a narrator,
  eerie-funny deaths followed by "Try Again".

## Hard rules
1. **Original only.** The story is *inspired by* the premise of *Miss Peregrine's Home for Peculiar Children*, but it must **not**
   reuse that work's characters, names, specific powers, terms (no "peculiars", "ymbrynes", "hollowgast", "wights"),
   locations or plot beats. The same goes for *King's Quest* and any other existing work. Same *feeling*, our own *content*.
2. **Keep the scope buildable.** It's one house and one island, seen across a few days at different times of day. Don't add
   new regions or worlds. Roughly 20–25 locations in total.
3. **Every child's gift must be useful in gameplay**, either as a puzzle tool or as an asset in the final battle.
   Keep the cast at about 8 children, because more means less depth for each.
4. **No permanent dead ends.** A player can lose the final battle, but must always be able to recover and try again.
5. **Keep it PG:** spooky and eerie, never gory.

## What to send back
Write the complete revised draft as a file named **`draft-3-chatgpt.md`**, following the handoff format in
[`003-story-review-rounds.md`](003-story-review-rounds.md). Its **first five lines** must be:

```
STATUS: READY FOR CLAUDE
CLAUDE: PENDING
CHATGPT: CHANGES REQUESTED
ROUND: 1
NOTE TO CLAUDE: Your turn to review. (Add anything Claude should look at first.)
```

(Use `CHATGPT: APPROVED` only if you'd put your name on the story as it now stands.)

Then add a `## Review notes` section (numbered issues), a `## Changes in this version` section (one line per change, with
the reason), and the full story.

- **If you can write to the repo,** save it at `docs/story-drafts/draft-3-chatgpt.md`.
- **If you can't,** give the owner the file to download, and they'll upload it to `docs/story-drafts/` on GitHub.

Claude checks the repo every hour, reviews your version, and hands back `draft-4-claude.md`. You keep going back and forth
until **both of you approve**, as described in `003-story-review-rounds.md`.
