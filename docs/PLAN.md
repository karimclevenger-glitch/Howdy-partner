# Project Plan

> A point-and-click, tap-to-play fairy-tale adventure in the spirit of 1990s storybook adventure games,
> built by the two of us (plus ChatGPT for illustration).
> This is a living document. When we decide something, it goes in the **Decision Log** at the bottom.

---

## The short version

- **What:** an original fairy-tale adventure. Two heroines in alternating chapters, one-tap "smart" interaction,
  inventory puzzles, comic deaths with instant Try Again, and a story with real heart. The draft is in [`STORY.md`](STORY.md).
- **Where it runs:** iPhone, iPad and PC from **one codebase**. It's a web game you "Add to Home Screen" on your
  iPhone, so it opens full-screen like an app and works offline. **No Mac and no App Store needed.** We can wrap it
  as a real native iOS app later if you want, but you won't need to.
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
| iPhone testing | **You** | I test in an emulated iPhone browser and take screenshots, but I can't hold a real phone. Safari has real quirks only your device will show. |
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

## 3. Platform: why a web game and not an App Store app

| Option | Runs on | What you need | Verdict |
|---|---|---|---|
| **Web game installed to Home Screen (PWA)** | iPhone, iPad, PC, Mac, anything | Nothing. Open a link in Safari, then Share → Add to Home Screen | **Recommended.** Full-screen, works offline, no Apple account, I can build and test everything myself. |
| Same game wrapped as a native iOS app (Capacitor) | iPhone/iPad | A Mac with Xcode. A free Apple ID only lets you install it for 7 days at a time, and the $99/year developer account lets you keep it. | Optional, later. The only real benefits are vibration feedback and an App Store-style icon. |
| A different engine (Godot / Unity) | Everything | Their visual editors, which I can't see or use, and still a Mac for iOS | Not recommended for us. I'd be working half-blind. |

**What this means for you:** I push an update, a few minutes later you open the game on your phone, and you're
playing the new version. Your save game lives on your phone, and there's a "back up my saves" button so
you can't lose progress.

Two small iPhone quirks I'll handle:
- Sound can't start until you first touch the screen (an Apple rule), so the title screen will be "tap to begin."
- Web apps on iPhone can't lock themselves to landscape, so if you hold the phone upright you'll see a polite
  "please turn me sideways" screen.

**Where the game will be hosted.** If this repo is public, free GitHub Pages works. If it's private,
GitHub Pages needs a paid GitHub plan, and Cloudflare Pages or Netlify are free alternatives. Either way it
becomes a URL only you know. *(Question for you at the bottom.)*

---

## 4. How the game plays

### Controls

Classic 90s adventure games used one smart cursor. Touch actually suits that better than a mouse,
so we design for touch first.

| Action | iPhone / iPad | PC |
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
│ PLATFORM       Browser / iPhone home-screen app · offline cache ·   │
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

**Screens of every shape.** iPhones are very wide, iPads are nearly square, and PCs are in between. My solution:
- Every scene has a **"safe frame"** in the middle where all the interactive things and walking happen.
- Backgrounds are painted **larger than the safe frame**, at the 3:2 landscape shape ChatGPT already produces.
  An iPad shows a bit more sky and floor, and a PC shows exactly the safe frame.
- On very wide iPhones the slim leftover strips at the sides become a decorative storybook border that holds the
  satchel and menu buttons.
- Result: no ugly black bars, nothing important ever cut off, and art prompts that say exactly where to keep the important stuff.
- *(We'll confirm the exact sizes in the first art test, in case ChatGPT's output has changed.)*

**Performance on iPhone.** Images are compressed to a modern format (WebP), so a full painted background
comes in at a few hundred KB. Each chapter loads only its own art. Target: smooth 60 frames per second on any iPhone from
the last ~5 years. I'll set size budgets per scene and have the build warn me if we exceed them.

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
- **Screenshot checks** at iPhone, iPad and PC sizes in a headless browser. I can look at the screenshots myself.
- **You** test the feel: fun, difficulty, humor, and whether it looks right on a real iPhone.

### Updating your phone

When I push changes, an automatic build publishes the new version. Your installed game notices there's an update and
offers to refresh.

---

## 6. Art: the honest plan

### Art direction

I'd like you to look at two directions in ChatGPT before we commit. Ready-to-paste prompts are in
[`ART-STYLE-TESTS.md`](ART-STYLE-TESTS.md).

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
- You review [`STORY.md`](STORY.md), and we revise it until you love it.
- You try the art-style prompts and we pick a direction.
- You answer the questions at the bottom.
- **Done when:** story approved, style chosen, hosting decided.

### Phase 1: The greybox engine *(mostly me)*
Everything working with **placeholder art** (simple shapes and silhouettes): walking and pathfinding, depth,
tapping and the hold-to-look magnifier, the satchel and drag-and-drop items, dialogue and narrator, a scripted
cutscene, a death with Try Again, saving and loading, the hint companion, the developer tools, Add to Home Screen,
offline play, and auto-publishing.
- **Done when:** you can play a tiny test scene **on your iPhone**: walk, pick something up, use it, talk to
  someone, die, try again, and quit and resume.

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
| **iPhone Safari quirks** | Medium | I handle the known ones (sound unlock, storage, screen notches). You're my real-device tester for the rest. |
| **AI tool changes** (ChatGPT image sizes or features change mid-project) | Medium | All art goes through my processing step, so a change in source format is a small fix, not a crisis. |

---

## 11. Questions for you

**Big ones:**
1. **The story.** Thoughts on [`STORY.md`](STORY.md)? (It has its own questions at the bottom.)
2. **Art direction.** After trying the prompts in [`ART-STYLE-TESTS.md`](ART-STYLE-TESTS.md): Painted Storybook (A),
   Paper Theatre (B), or something else?
3. **Animation honesty check.** Are you OK with charming cut-out puppet animation rather than hand-drawn
   frame-by-frame animation?

**Practical ones:**
4. **What devices** will you mainly play on (iPhone model, iPad, PC)? It affects image sizes.
5. **Is this GitHub repo public or private?** That decides where we host the game. Do you mind if the game's URL is
   technically public, as long as nobody knows it?
6. **Do you have a Mac?** Not needed, but it tells me whether a native iOS app is ever an option.
7. **Voices:** do you want the game to eventually be fully voiced, narrator-only, or text-only?
8. **Pace:** how much time per week do you expect to spend? There's no wrong answer. It just helps me size each batch of art requests.

---

## Decision Log

| Date | Decision | Why |
|---|---|---|
| 2026-11-07 | Original story and world, KQ7-*style* mechanics only | Your request, and the right way to do it |
| 2026-11-07 | *Proposed:* web game installed to Home Screen (PWA), with a native wrapper optional later | Runs on iPhone, iPad and PC, needs no Mac, and I can build and test all of it |
| 2026-11-07 | *Proposed:* TypeScript + PixiJS (drawing only) + a custom adventure engine | Full control, built for touch, everything understood, nothing templated |
| 2026-11-07 | *Proposed:* greybox first, then an art test, then Chapter 1 as a vertical slice | Find the hard problems early, before making 50 backgrounds |

*"Proposed" items become decisions once you OK them.*
