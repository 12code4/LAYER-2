# Doodle Pad — design notes

> A pad for drawing. Whatever you draw is alive. After a while, it draws back.
> Pointer only. No text. No hints. (Internal codename: NULLPAD.)

For readers of the source, not players. Players get none of this — that's the point.

---

## 0. The brief this answers

Third game in the repo. The user's direction across three tries narrowed hard:
**"go crazier, wackier — more freedom, more input"** and then, twice,
**"don't make it a typing game."** So the whole input surface is the pointer, and the
verb is *drawing* — the highest-freedom, most universally legible non-keyboard input there is.
It still obeys the standing brief from the research corpus (`docs/research/notes` in
`12code4/layers`): **hide the hand entirely, no hints, the player pulls at the seams.**

It descends most directly from **Duck Amuck** (Chuck Jones, 1953) — the one ancestor in the
research where an unseen animator torments a *drawn* character, then is revealed as another
character (A1 §1). Doodle Pad inverts it: **you** are the animator, the drawing gets a say,
and in the end the hand that draws is revealed to be drawn too.

## 1. How it was built (multi-agent, then hand-authored)

Design came from a **Workflow**: five parallel design lenses (wacky mechanics, hidden-hand
escalation, pointer-input, tech feasibility, novelty/tone) → a synthesized build spec → an
adversarial critique. The critique caught five real problems *before* a line was written; all
five are baked in (below). I authored the game from that spec. A second review workflow was
attempted but blocked by an environment permission bug in the subagents, so the code review was
done by hand + headless-browser testing (Playwright driving the pointer through the whole arc).

## 2. The sincere toy first (the DDLC / "earn the love" rule)

- **Papers:** A1 §6.4, A3 §5.1, B5 §1.5–1.6; spec WOW #1–3.
- Draw freehand → every stroke becomes a googly-eyed creature: velocity→width ink ribbon
  (capsule-stamped, round caps), spring-lag pupils that overshoot when the body accelerates,
  idle breathe/wobble, drop shadow, squash/stretch, gravity + floor bounce, hop, and
  **ducklings** (they conga after the cursor). Colour silently drives temperament
  (red hot, blue sleepy, green social, yellow bouncy) — inferred, never stated. It has to be a
  genuinely fun fidget toy before anything turns, or the ending costs nothing.

## 3. The five critique fixes (baked in)

1. **Erase is a selected tool, not a gesture** — tap the kneaded-eraser in the tray. This kills
   the "frantic scribble vs. scrub-erase" collision and the "sleep-hold vs. erase-hold" collision
   the critique found, and makes erasing *deliberate*.
2. **Erasing settled ink is neutral; only rubbing out an *alive, fleeing* creature counts**
   (`erasedAlive`). Correcting a doodle must never be branded cruelty (the critique's sharpest
   ethics catch). Accountability needs a genuinely optional cruel act.
3. **The first stroke always gets the full "First Breath"** (guaranteed eyes/blink/hop),
   regardless of geometry — the universal gasp is never wasted on a stroke that classifies as a
   dot that skitters off.
4. **Self-demonstrating fun early** — a resting "bait" doodle toddles toward the cursor so a
   hesitating player sees aliveness with zero text; ducklings/separation make a society emerge.
5. **No tells in the opening minutes** — no title/favicon change, no frame-breaks, no cursor
   drift early; the *first* unprompted mark the pad makes is a **drawn heart** (sweet disarms the
   pre-braced player far better than a scare). Reveal choreographed tender, not menacing.

## 4. The turn (Duck Amuck, inverted) — enacted, never narrated

One `agency` scalar + a persisted ledger (`localStorage doodle.v1`) drive stages, gated by
**player action + soft time floors** so a frantic scribbler and a careful drawer both hit each
beat (B2/B3). No on-screen text at any point — every message is made of bodies, eyes, and marks.

1. **Toy.**
2. **Will** — bring the (selected) eraser near a creature and it flees intelligently; spare one
   and it follows you like a puppy. (A5 accountability; B4 refusal.)
3. **The pad draws back** — on an idle *lull*, a stroke lays itself down point-by-point at
   hand cadence, in *your* palette, then comes alive. "Did I draw that?"
4. **The mimic** — a creature watches your last shape and draws it back, slightly wrong. The
   first *undeniable* "it can draw, and it learned from me."
5. **The other hand** — a second, heavier cursor appears, redraws, and gently *ablates* channels
   (desaturates, "tidies" your wobbly lines) — always restored within seconds, never a fake crash.
6. **The inversion** — the camera pulls back: your whole pad is one small sheet among thousands of
   faint marks on a vast pad, a giant pencil pausing above it. Your own cursor is now a mark with
   a shadow and eyes; move to the edge and it flinches from the giant exactly as the creatures
   flinched from your eraser. (Hofstadter strange loop, B4 §6; Turing inversion, A4 §7.)

## 5. Endings (pointer only, consensual)

The giant sets its eraser down beside your mark — an **offer**, not a threat — and you get a real
window to choose (never sprung on you):
- **Merge** (gentle default, low cruelty): do nothing; the creatures gather to your mark, all
  eyes turn outward together, hearts rise. Relation changed from user-of-tool to one-mark-among-many.
- **Erase** (the one reserved, real, consensual cost — NieR Ending E, A5 §3.6): deliberately
  *pick up* the offered eraser, then a slow ≥2-second hold-drag. It genuinely clears the game's
  own `localStorage` (only `doodle.*`), unrecoverable; each creature gives a farewell hop + heart
  and dissolves; the page goes blank. A scar is left so a later "fresh" pad remembers, faintly.
- **Accountability** (high `erasedAlive`): merge is never offered; the erase gets no farewell wave.

**The consent bug I caught in self-review:** the hold-drag erase originally counted *any* held
drag during the finale, so a player merely drawing could delete everything. Fixed: drawing is
disabled once you're a mark, and the erase only counts after the offered eraser is actually
picked up. And merge no longer fires the instant it's offered — there's a window, and it won't
fire while you're reaching for the eraser.

## 6. Rails (hidden) + accessibility

- The lie is only about **authorship/meaning**, never data. The only real destruction is the
  consensual erase of the game's own keys. No fake browser/OS crash, no fake file-delete.
- `prefers-reduced-motion`: damped wobble/breath, a gentle crossfade-ish zoom, no strobing, no
  full-canvas flashes.
- DPR capped at 2; awake-souls capped (~36, others sleep) so it holds framerate; particles capped;
  `visibilitychange` pauses the loop; `localStorage` wrapped in try/catch (private mode).
- Pointer-only, one code path for mouse/touch/pen; no keyboard, hover, or right-click ever
  required; tray hit areas padded; touch uses the finger as the cursor.

## 7. Files

- `doodle/index.html` — the whole game (self-contained vanilla JS + canvas, no deps, no network).
- `doodle/DESIGN.md` — this document.

`?fast` accelerates the arc and exposes `window.__dbg()` — for development and the impatient.
