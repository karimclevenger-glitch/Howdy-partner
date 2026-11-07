# Project Plan

> A point-and-click, tap-to-play fairy-tale adventure in the spirit of 1990s storybook adventure games,
> built by the two of us (plus ChatGPT for illustration).
> This is a living document. When we decide something, it goes in the **Decision Log** at the bottom.

---

## The short version

- **What:** an original fairy-tale adventure. Two heroines in alternating chapters, one-tap "smart" interaction,
  inventory puzzles, eerie-funny deaths with instant Try Again, and a story with real heart. The current story draft is
  [`story-drafts/draft-2-morrow-isle.md`](story-drafts/draft-2-morrow-isle.md): an island time loop, a bird-headmistress,
  a house of unusual children, and invisible monsters.
- **Where it runs:** **PC first**, in your web browser (or installed as a desktop app icon from Chrome or Edge).
  Because it's a web game, the **same code also runs on your phone** as a bonus. **No Mac and no App Store needed.**
- **Who does what:** I design, write, and build **all the code, tools, story, dialogue and puzzles**, and I write
  every art prompt. **You** are the creative director and playtester, and the bridge to ChatGPT and Runway.
  ChatGPT paints the art. Runway animates a handful of big cinematic moments.
- **How we work:** short loops. I build something, you play it on your phone, you tell me what you feel, and I fix it.
  We start with a **greybox** (placeholder shapes) so the game *plays* right before it *looks* right.
- **The biggest honest risk:** consistent, animated **character art** from AI image tools. Our first art test is
  designed to find out early what works (details below).

---

## 1. A quick, honest note about King's Quest VII

You said the company no longer exists, so it should all be free to use. One correction: Sierra was bought,
and the King's Quest series is still owned (today it sits under Microsoft, via Activision). That doesn't
actually limit us. **Nobody owns a genre.** Point-and-click mechanics, inventory puzzles, alternating heroines,
comic deaths and fairy-tale settings are all fair game. What we won't do is copy that game's story, characters,
names, places, puzzles, dialogue, art or music. You'd already asked for a rewritten story, so we want the same
thing: **a game that gives you that feeling, while being entirely its own.**

---

## 2. Who does what

| Area | Who | Notes |
|---|---|---|
| Game engine, all gameplay code, UI, saves, tools | **Me** | My strongest area. Written specifically for this game, not a template. |
| Story, world, characters, dialogue, narrator jokes, deaths | **Me**, with your approval | Writing is a real strength. You have veto and final say on all of it. |
| Puzzle design | **Me**, with your playtesting | I can design fair, clever puzzles. **Only a human playing can tell us if they're fun or too hard.** That's you. |
| Art direction (style guide, palettes, shot composition) | **Me + you** | I write the style bible and every prompt. You choose what you like. |
| Painting backgrounds, characters, items, portraits | **ChatGPT** (you run the prompts) | I can't make painted illustration at this quality myself. I *can* look at every image you send and give specific feedback. |
| Character animation (walking, talking, reaching) | **Me**, in code | I animate characters as layered "cut-out" puppets in code. See §6 for the honest version of what that looks like. |
| Background life (water shimmer, fireflies, falling sparks, lantern flicker) | **Me**, in code | Cheap, light on the phone, and I can do it well. |
| Cinematics (intro, big twist, ending) | **Runway** (you run my shot list) + **me** assembling | Good for a few showpiece moments. Not suitable for in-game character animation (explained in §8). |
| Placeholder art and UI (menus, inventory frame, icons) | **Me** | Simple vector graphics I can make myself. Final UI can be restyled with ChatGPT art. |
| Music | **Recommended: Suno** (AI music) | I can write the music-box melody and simple chimes myself. I can't produce a full score at a quality you'd be proud of. |
| Sound effects | **Free libraries** (freesound.org, Sonniss GDC bundles) or **ElevenLabs** | I can find, trim, and mix them. |
| Voice acting | **Optional, later: ElevenLabs** | The game is built subtitles-first. Voices can be added at the end without changing anything. (If you ever get an ElevenLabs API key, I can generate every line myself in one go.) |
| Real-device testing | **You** | I test in a real browser here (the same engine as Chrome and Edge on your PC) and take screenshots I can look at. I can't hold your phone, so phone checks are yours. |
| Talking to ChatGPT | **Through the repo** | ChatGPT is connected to this repo. Every request I make of it lives in [`prompts/`](../prompts/README.md), so you just point ChatGPT at a file. |
| Native iOS app (optional, only if wanted) | **You need a Mac with Xcode** | I can't run Xcode from here. This is why the plan is designed not to need it. |

### Tools: what you have, what I'd add

- **ChatGPT (image generation).** Essential. It's our illustrator.
- **Runway.** Useful, but in a supporting role: cinematics and maybe a few animated background loops.
- **Suno**, *recommended* for music. You describe a mood and get a track. Fine for a personal project.
- **ElevenLabs**, *optional*, for voices and sound effects, near the end of the project.
- **Photopea** (free, works in a browser), *only if needed*, for touching up an image (e.g., erasing a stray artifact).
- **An upscaler** (e.g., Upscayl, which is free), *only if needed*, if ChatGPT's images come out too small for crisp iPad display.
- **Nothing to install for me.** My side is all set up here.

---

## 3. Platform: PC first, phone as a bonus

**Decided:** you have a PC and a phone, and you're happy with PC-only if that makes a better game. It does, in specific ways:

- **Real mouse hover.** The classic adventure-game feel, where the cursor changes as it passes over things you can
  interact with, only exists with a mouse.
- **A big screen.** More painted detail visible, characters drawn larger, comfortable text.
- **I can test exactly what you'll play.** The browser I test in here is the same engine as Chrome and Edge on Windows.
- **Fewer compromises.** Every design decision gets made for the mouse first.

Because it's a web game, **choosing PC first doesn't cost us the phone.** The same game still runs on your phone with
touch controls. I just won't bend the PC version out of shape to fit a small screen.

| Option | Verdict |
|---|---|
| **Web game, played in Chrome or Edge on your PC** (optionally "installed" so it gets its own desktop icon and window) | **Chosen.** Nothing to install, auto-updates, and I can build and test everything myself. |
| The same game on your phone's browser | A free bonus, kept working but not the priority. |
| A native desktop app (a wrapper around the same game) | Possible later if you want a double-click icon that feels like a "real" program. Not needed. |
| A different engine (Godot / Unity) | Not recommended. Their visual editors are something I can't see or use, so I'd be working half-blind. |

**What this means for you:** I push an update, you refresh the game in your browser, and you're playing the new
version. Your saves live in your browser, and there's a "back up my saves" button so you can't lose progress.

**Hosting (where the game lives online).** The project now lives in **`karimclevenger-glitch/Howdy-partner`**, which is
**public**. That means free GitHub Pages hosting works, and I'll set it up when there's a first playable build. The trade-off
is that anyone who finds the repo can see the story, the art, and the email address on its first commit. If you'd rather
keep it private, switch it in the repo's Settings → General → "Change visibility", and I'll use a free private-friendly host
(e.g., Cloudflare Pages) instead.

---

## 4. How the game plays

### Controls

Classic 90s adventure games used one smart cursor that changes as you move over things. **The mouse on PC is our main
target.** Touch on the phone gets an equivalent for every action.

| Action | Phone (touch) | PC (mouse, the main target) |
|---|---|---|
| Walk | Tap the ground | Click |
| Do the obvious thing (talk, take, open, use, go through an exit) | **Tap** it | Click |
| Look at / describe something | **Press and hold, then drag.** A magnifier floats *above* your finger (so your thumb doesn't hide it) and shows each thing's name. Let go on a thing to hear the narrator describe it. | Right-click (and hovering shows names) |
| Find everything I can interact with | Tap the ✨ button and every hotspot sparkles for 2 seconds | Same, or the Tab key |
| Hurry | Double-tap to run, or to skip straight through an exit | Double-click |
| Use an item | Open the satchel, then **drag the item onto something** (or tap the item, then tap the target) | Same |
| Combine items | Drag one item onto another in the satchel | Same |
| Inspect an item up close | Double-tap it in the satchel and a close-up opens. Items can hide secrets: open a locket, turn a map over. | Double-click |
| Hint | Tap your companion (Admiral Pinch or Dimity). The first tap is a nudge, the next is clearer. | Same |
| Skip dialogue / cutscene | Tap to skip a line. A ⏭ button skips a whole scene. | Click / Esc |

Every tappable thing gets a touch target at least finger-sized, even if the object itself is tiny in the painting.

### The rules of a good adventure game (our design commandments)

1. **No dead ends, ever.** You can never get permanently stuck because you missed something earlier.
   (Older games in the genre did this to players. We won't.) I'll write an automated checker that
   proves it for every chapter.
2. **Deaths are jokes, not punishments.** Every death plays its gag, gets a narrator line, and offers
   **Try Again**, which puts you back just before the fatal choice.
3. **Every puzzle is clued twice.** At least two in-world hints point to each solution: a description,
   a line of dialogue, something in the background art.
4. **Whimsical, but consistent.** Fairy-tale logic with rules that never break (e.g., "the lighthouse beam makes
   glass remember it's water"). Once you learn a rule, you can trust it.
5. **More than one thread at a time.** Each chapter has two or three puzzle threads you can work on in any order,
   so being stuck on one never means you're stuck on everything.
6. **Wrong guesses get rewarded with jokes.** Trying a silly item on a silly target should get a custom line as often as
   possible, not "That doesn't work." That's what makes a world feel alive.
7. **The narrator has something to say about everything,** including things that aren't puzzles.

### Saving

- **Autosave** every time you enter a new scene, plus **manual save slots**.
- **Try Again** is a separate checkpoint taken right before anything dangerous.
- **Chapter select** unlocks as you finish chapters.
- **Back up / restore saves** as a small file, in case your phone ever clears its storage.

### Comfort settings

Text size, text speed, always-on subtitles, separate music/sound/voice volumes, "always show hotspot names,"
and reduced motion. There are no timed puzzles except a couple of short, forgiving action moments
(the Long Wave slide and the finale rhythm) that can be retried instantly.

---

## 5. Under the hood (the technical design)

This section is for you to *understand* how the game works. You don't need to read code to follow it.

### Building blocks

- **TypeScript.** A careful dialect of JavaScript that catches mistakes before you ever play.
- **PixiJS.** A proven, very fast 2D graphics library for drawing things on screen. I use it **only** to draw.
  Everything that makes this an adventure game is written by me, for this game.
- **Vite.** The build tool that turns the code into the files your phone downloads.

That's deliberate. I'm not using an adventure-game kit or template. I am using a solid drawing library,
because writing my own graphics driver would add risk and give us nothing.

### How it's organized

```
┌─────────────────────────────────────────────────────────────────────┐
│ CONTENT        Story chapters: scenes, items, characters, puzzles,  │
│                dialogue scripts, deaths                             │  ← changes most
├─────────────────────────────────────────────────────────────────────┤
│ ADVENTURE      Scenes & hotspots · walking & pathfinding · depth    │
│ ENGINE         scaling · inventory · dialogue & narrator · cutscene │
│                scripting · deaths & Try Again · saves · hints       │
├─────────────────────────────────────────────────────────────────────┤
│ CORE           Game loop · drawing (PixiJS) · touch & mouse ·       │
│                sound · loading · tweening/animation · screen sizing │
├─────────────────────────────────────────────────────────────────────┤
│ PLATFORM       Browser on PC (or phone) · optional install ·        │
│                storage                                              │  ← changes least
└─────────────────────────────────────────────────────────────────────┘
```

### The key pieces, explained

**Scenes (rooms).** Each scene is one painted background plus data: where you can walk, what's tappable,
who's standing where, where the exits go, and what happens on entry. Scenes are short, readable files,
one per scene.

**Where you can walk.** Each scene has a **walk area**, an invisible shape drawn over the floor of the painting,
possibly with holes for rocks, tables, and so on. When you tap a spot, the game finds the shortest route around
obstacles. (This is a classic technique: route between the corners of the walk area.) If you tap somewhere
unwalkable, you walk to the nearest reachable point.

**Depth.** Characters get **smaller as they walk "into" the picture** and bigger as they come toward you, based
on how high they are on screen. Each scene has its own setting so this matches the painting's perspective.
Things in the foreground, like a tree trunk or a ship's railing, are separate layers so characters can walk
*behind* them.

**Scripting with a "screenplay" feel.** Story moments are written as step-by-step scripts that read like stage
directions: walk here, turn, say this line, wait, give the item, play the animation. Any cutscene can be
skipped, and skipping leaves the game in exactly the right state (this is harder than it sounds, and it's built in
from day one).

**Dialogue lives in screenplay files** you can read and edit yourself:

```
== glasswater.gull.first_meeting
GULLINGSWORTH: Halt! State your name, species, and preferred filing category.
TAMSIN: I'm… lost?
GULLINGSWORTH: Lost! Splendid. That's Form L-0-5-T. In triplicate.
NARRATOR: Tamsin had never been filed before. She suspected she was about to be.
```

Every line gets a unique ID automatically, so voice acting can be added later without touching the game.
A checker makes sure every line referenced in the game exists, every speaker is a real character, and no line is too
long for the subtitle box.

**One source of truth for "where you are in the story."** Everything (inventory, what you've done, who you've
talked to, where everyone is) lives in one place that gets saved. Story flags have exact names that the code checks
before you ever play, so a typo can't silently break a puzzle.

**Screen shape.** The game is designed for a standard **16:9 PC screen** (1920×1080 and up).
- Every scene has a **"safe frame"**, the 16:9 area where all the interactive things and walking happen.
- If ChatGPT gives us 3:2 images instead of 16:9, the extra strip at the top and bottom gets trimmed, which is why every art
  prompt says to keep the top and bottom 10% free of anything important.
- On a phone (wider than 16:9), the slim leftover strips at the sides become a decorative storybook border that holds the
  satchel and menu buttons. No ugly black bars, and nothing important cut off.
- *(We'll confirm the exact image sizes in the first art test.)*

**Performance.** Images are compressed to a modern format (WebP), so a full painted background comes in at a few hundred KB.
Each chapter loads only its own art. Target: smooth 60 frames per second on an ordinary PC, still smooth on a recent
phone. I'll set size budgets per scene and have the build warn me if we exceed them.

### My development tools (built into the game, hidden from players)

These tools are what make the project doable. With a secret developer switch on:

- **Scene editor overlay.** Draw and adjust walk areas, hotspots, depth scaling and exits *directly on top of the
  painting*. **You can use it too**, right on your iPad if you like, so you can drag a hotspot to exactly where the
  lantern is. The changes save as data I bring into the code.
- **Debug view.** Shows walk areas, routes, hotspot outlines and frame rate.
- **Cheats.** Jump to any scene, give yourself any item, set any story flag. That makes it fast to test chapter 5
  without replaying chapters 1–4.
- **Puppet tuner.** Adjust where a character's joints bend, live.

### Testing (so you're not my bug-finder)

- **Automated playthroughs.** For every chapter, a script plays the whole thing start to finish through the game's
  logic. If a change ever makes a chapter impossible to finish, I find out before you do.
- **The no-dead-ends checker.** Each chapter's puzzle chart is written down as data, and a tool proves every goal can still be
  reached from every state.
- **Screenshot checks** at PC and phone sizes in a headless browser. I can look at the screenshots myself.
- **You** test the feel: fun, difficulty, humor, and whether it looks right on your PC and phone.

### Updating your phone

When I push changes, an automatic build publishes the new version. Your installed game notices there's an update and
offers to refresh.

---

## 6. Art: the honest plan

### Art direction

I'd like you to look at two directions in ChatGPT before we commit. Ready-to-paste prompts are in
[`prompts/001-art-style-tests.md`](../prompts/001-art-style-tests.md), which also explains each style in plain words.

**A. Painted storybook (my recommendation)**
Lush hand-painted backgrounds (gouache and watercolor texture) with characters in **clean outlines and flat colors
with one soft shade**, the look of a classic animated fairy tale. This isn't just taste. It's practical:
- Flat-colored, outlined characters are **far easier for AI to draw consistently** from image to image than painterly ones.
- They're also much easier to cut into puppet pieces that bend cleanly.
- Painted backgrounds can be as rich as ChatGPT can manage, because they never need to move.

**B. Paper theatre / pop-up book**
Everything looks like layered cut paper with soft shadows between layers. It's very charming, and puppet animation looks
100% *intended* in this style. It's less "classic animated fairy tale," though.

### How characters will move (please read this one)

Characters in 90s adventure games were **hand-animated frame by frame** by teams of professional animators.
**Current AI image tools can't reliably produce frame-by-frame animation of the same character**. They
drift: the coat changes, the face shifts, the cane moves to the other hand. So here's what I propose:

**Cut-out puppet animation.** Each character is delivered as separate pieces (head, body, upper arms, forearms,
legs, plus a few mouth shapes and a blink), and I animate them in code: walking, idle breathing, talking,
reaching, picking things up, being startled, and a few special moves per death gag. Each character gets a
**side view** (mirrored for left/right), a **front view** and a **back view**.

- **What it looks like:** like quality modern cut-out animation. Smooth, expressive, charming, clearly
  storybook. **Not** like hand-drawn Disney-style animation. I want you to know that going in.
- **Why it works:** you only need to generate a character's pieces once, and every animation reuses them, so the
  character always looks exactly the same.
- **Backup plan** if puppet pieces prove too fiddly to get from ChatGPT: "pose-to-pose" style. Each character gets
  10–15 full-body pose images (stand, step, reach, talk, and so on) that I blend between with squash, bob and sway.
  It's simpler to generate, but looks a bit more like a pop-up book.

**The very first art test answers which one we use**, before we've committed to anything.

### How you'll get images to me

- **Quick opinions** ("which of these do you like?"): just paste images into our chat. I can see them.
- **Final assets:** upload them to the **`art-inbox/`** folder in this repo (on GitHub: open the folder,
  then Add file → Upload files). Name them however you like and I'll rename, resize, compress, cut out
  pieces, and file them properly.
- For each chapter I'll give you an **asset checklist**: every prompt, the exact shape and size, what must be
  on a plain background, and what to name it, so it's never a guessing game.

### Rough art budget for the whole game (so there are no surprises)

| Type | Approx. count | Notes |
|---|---|---|
| Backgrounds | 45–50 | The biggest job. Expect a few tries each. |
| Foreground layers | ~30 | Pieces characters walk behind. Not every scene needs one. |
| Main characters as puppet pieces | 3 (Tamsin, Beatrix, Celandine plus her Linnet disguise) | The fiddliest job, done once, early. |
| Supporting characters | ~20 | Many can be simpler (fewer views, and a few just need idle + talk). |
| Inventory items | ~60 | Quick and easy. |
| Talk portraits | ~25 | For the dialogue box. |
| Death "storybook cards" | ~30 | One illustration per death, shown with the narrator's line. |
| Chapter title pages | 8 | |

This is **months of steady, part-time work** on the art side, mostly yours, running prompts and picking winners.
That's the real bottleneck of the project, not the code. My job is to make each request precise enough that you
rarely have to redo one.

---

## 7. Sound and music

- **Music:** one theme per region plus a few story themes. I'll write a detailed music brief per track for Suno
  (mood, instruments, tempo, "should loop seamlessly"). I can compose and produce **the music-box melody of the
  rhyme** myself, since that's simple enough to do well in code, and it ties the whole score together.
- **Sound effects:** sourced from free libraries, plus a few small UI sounds I make myself.
- **Voices:** subtitles-first. Adding voice acting is a late, optional phase. A narrator voice alone would be a
  lovely middle option.

---

## 8. Cinematics

- **Most story moments happen in the game engine** with the same puppets and backgrounds, plus camera moves,
  lighting, and storybook-style framing. This keeps everything consistent and is fully in my hands.
- **Runway for 3–5 showpieces:** the opening (the music box, the fall into the sunset), maybe the twist, and the dawn
  ending. Runway works best when we give it **our own ChatGPT art as the starting frame**, so it matches the game.
  I'll write the shot list and every prompt, and I can assemble the clips with music and sound here.
- **Honest limits of Runway:** keeping characters consistent across separate clips takes trial and error, it produces
  full video rather than characters with transparent backgrounds (so it can't drive in-game animation), and video files
  are large, so we use it sparingly.

---

## 9. Roadmap

Each phase ends with something **you can play or look at**, and a check-in where you tell me how it feels.

### Phase 0: Foundations *(we're here)*
- **Story pitch round:** a fresh set of story pitches written the way a game writer works. You pick and mix, then we develop the winner until you love it.
- You try the art-style prompts and we pick a direction.
- You answer the questions at the bottom.
- **Done when:** story approved, style chosen, hosting decided.

### Phase 1: The greybox engine *(mostly me)*
Everything working with **placeholder art** (simple shapes and silhouettes): walking and pathfinding, depth,
tapping and the hold-to-look magnifier, the satchel and drag-and-drop items, dialogue and narrator, a scripted
cutscene, a death with Try Again, saving and loading, the hint companion, the developer tools, Add to Home Screen,
offline play, and auto-publishing.
- **Done when:** you can play a tiny test scene **on your PC** (and it also works on your phone): walk, pick something up,
  use it, talk to someone, die, try again, and quit and resume.

### Phase 2: The art test *(you + me)*
One real Glasswater background, Tamsin built as a puppet, one supporting character, one item.
- **Done when:** Tamsin walks around a real painted scene on your phone and it looks like *our game*.
- **Decision point:** puppet animation vs. pose-to-pose, and the exact image sizes.

### Phase 3: Chapter 1, the first full chapter
Detailed chapter design → your approval → full asset checklist → you generate, I build → you play it start to finish.
- **Done when:** Chapter 1 is complete, funny, fair, and you're proud of it.
- **Then:** we look at how long it *actually* took and adjust the plan for the rest of the game, honestly.

### Phase 4: Prologue + Chapter 2
Beatrix's tools (cane, ear-trumpet) and the Ember Wood.

### Phase 5: Chapters 3–4
Tamsin's glow, the mole-folk, and the shadow puppetry of Hushwater.

### Phase 6: Chapters 5–6 + ending
Switching between the two heroines, the twist, the rhythm finale, the epilogue.

### Phase 7: Polish
Music and sound pass, optional voices, Runway cinematics, the Lark Feathers extras, full playthroughs,
comfort settings, and (optional) the native iOS wrapper.

---

## 10. Risks, said plainly

| Risk | How likely | What we do about it |
|---|---|---|
| **Characters look different from image to image** | High | Flat-color style, a reference sheet per character that you attach to every prompt, the puppet approach, and an early test. |
| **Puppet animation doesn't feel right to you** | Medium | We find out in Phase 2, before building chapters, and switch to pose-to-pose if needed. |
| **Scope: this is a big game** | High | Chapter 1 first, then an honest re-plan. If we need to trim, we trim scenes, not story. |
| **I don't remember past sessions** | Certain | Every Claude session starts fresh. **Everything we decide gets written in this repo** (this plan, the story bible, the decision log, and a `CLAUDE.md` I read first every time). If it isn't written down, I won't know it. |
| **Puzzles too hard or too easy** | Medium | I design carefully, but only playtesting tells. Your reactions are the most valuable input in the project. |
| **Phone quirks** | Low priority now | PC is the main target. I'll keep the phone working (sound unlock, screen notches, touch), and you'll tell me if something's off. |
| **AI tool changes** (ChatGPT image sizes or features change mid-project) | Medium | All art goes through my processing step, so a change in source format is a small fix, not a crisis. |

---

## 11. Questions for you

**Still open:**
1. **The story.** We're doing a fresh pitch round (see the Decision Log).
2. **Art direction.** After trying [`prompts/001-art-style-tests.md`](../prompts/001-art-style-tests.md): Painted Storybook (A),
   Paper Theatre (B), Ink & Watercolor (C), or something else?
3. **Animation honesty check.** Are you OK with charming cut-out puppet animation rather than hand-drawn
   frame-by-frame animation?
4. **Voices:** do you want the game to eventually be fully voiced, narrator-only, or text-only?
5. **Pace:** how much time per week do you expect to spend? There's no wrong answer. It just helps me size each batch of art requests.

**Answered:**
- *Devices:* a PC and a phone, no Mac. PC is the main target (see §3).
- *Public or private repo:* your call was "either". The new repo is public, and you can switch it any time (see §3, Hosting).

---

## Decision Log

| Date | Decision | Why |
|---|---|---|
| 2026-11-07 | Original story and world, KQ7-*style* mechanics only | Your request, and the right way to do it |
| 2026-11-07 | **PC first** (mouse, 16:9). The phone keeps working as a bonus from the same code. | You have a PC and a phone and said PC-only is fine if it makes a better game. Mouse hover, a bigger screen and exact testing make it better. |
| 2026-11-07 | Web game (TypeScript), played in the browser. No App Store or Mac needed. | Runs everywhere, auto-updates, and I can build and test all of it myself |
| 2026-11-07 | All requests for ChatGPT (and later Runway) live in `prompts/`. ChatGPT reads them through its GitHub connection. | You connected ChatGPT to the repo, so you just point it at a file instead of copy-pasting |
| 2026-11-07 | Art style tests made story-neutral | The story is being re-pitched, so no art effort gets wasted |
| 2026-11-07 | Story Draft 1 ("The Long Dusk", grandmother and granddaughter) **not approved**. Fresh pitch round, written game-first. | You weren't loving it. You *did* like the "stuck in time" idea and want a Miss-Peregrine-style **repeating day/time loop** explored. |
| 2026-11-07 | **New story direction (yours):** an original game *inspired by the premise of* Miss Peregrine's Home for Peculiar Children. You travel to an island, enter a one-day time loop, meet a bird-headmistress who resets it, explore the house, help unusual children, build glasses to see invisible monsters, make weapons, and prepare for a final battle you can lose. | Your concept. We keep the premise and feeling but write our own characters, names, powers and plot (same rule as King's Quest). Draft 2 is in `docs/story-drafts/`. |
| 2026-11-07 | Story workflow: Claude drafts → ChatGPT reviews and revises (`prompts/002-story-review.md`) → Claude reviews ChatGPT's edits → you decide | Your idea, so two different writers each challenge the other |
| 2026-11-07 | Story review rounds: ChatGPT and Claude alternate numbered draft files in `docs/story-drafts/` (rules in `prompts/003-story-review-rounds.md`) until **both approve**, with a cap of 4 rounds each, after which the disagreements go to you. Claude checks hourly for ChatGPT's handoffs via a scheduled task. You give the final sign-off. | Your request: catch story holes and make the story full of adventures and puzzles |
| 2026-11-07 | Story handoff route (set up by ChatGPT, relayed by you): ChatGPT's drafts go to `main`; Claude's go to the `story-review-handoff` branch (PR #1, kept open). Claude checks every 15 minutes, with an hourly backup. | ChatGPT can publish to the repo directly, so you don't have to carry files between us |
| 2026-11-07 | **Story approved by both writers** (Claude and ChatGPT) after three review rounds. It's in `docs/STORY.md`, **awaiting your sign-off** and your answers on the title, the protagonist and the quiet ending. | The review loop you asked for, run until both approved |
| 2026-11-07 | **You sent "Morrow Isle" back** (not approved). New direction, in your words: the Haunters want the children's *powers*; the loop is something we learn about and protect from outsiders; every evening we watch the headmistress rewind time just before the danger strikes, and that danger is the final boss and the Haunters; names must mean something; it must be easy to follow. Claude's rewrite is `docs/story-drafts/draft-8-claude.md` ("Vesper House"), now with ChatGPT. | Your feedback. The story had turned into a rulebook. |
| 2026-11-07 | **Story rule from now on:** story first and readable in one sitting. Three loop rules at most, meaningful names, no rule jargon. Puzzle and mechanics detail goes in later chapter design docs. | Your feedback. Both writers had over-engineered it. |
| 2026-11-07 | *Proposed with Draft 2:* losing the final battle rewinds you to the morning of the last day, keeping your items and knowledge | Real failure without permanent dead ends, using the time loop itself as the safety net |
| 2026-11-07 | *Proposed with Draft 2:* scope drops to ~20–25 backgrounds (one house + island across days and lighting) | Far more achievable than Draft 1's six regions |
| 2026-11-07 | **Project moved to `karimclevenger-glitch/Howdy-partner`** (public). All work was carried over. The old repo's first commit was left out because it carried a personal email address. Claude pushes prompt and story files straight to `main`, so ChatGPT can read them without any pull requests. | GitHub was reconnected under a different account that can't see the old `KlarityK1` repo, and you asked for a new repo |
| 2026-11-07 | *Proposed:* TypeScript + PixiJS (drawing only) + a custom adventure engine | Full control, everything understood, nothing templated |
| 2026-11-07 | *Proposed:* greybox first, then an art test, then Chapter 1 as a vertical slice | Find the hard problems early, before making 50 backgrounds |

*"Proposed" items become decisions once you OK them.*
