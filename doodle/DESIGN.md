# Doodle Pad — design notes

> A little pad for drawing. Whatever you draw is alive.
> Pointer only — no keyboard, ever. It looks like a fidget toy. It is Duck Amuck.

For readers of the source, not players. **Players get none of this.** No text, no hints, no
warnings appear in the game itself; you find everything by pulling at it.

This game was designed by a multi-agent workflow (five design lenses → synthesis → adversarial
critique) and then hand-authored and verified in a headless browser. The spec's internal codename
was **NULLPAD**.

---

## 0. The brief it answers

Third in a series of hidden-hand metafictions built from the LAYERS research corpus
(`docs/research/notes` in the sibling `12code4/layers` repo). The first two — **CARET** and a
scrapped sandbox — were typing games; the user asked for something **crazier, with more freedom
and more input, and no typing at all.** So Doodle Pad is:

- **Pointer only.** Draw, grab & fling, poke, seed, pick a color, erase (a *selected tool*), undo
  (the dog-ear). No keyboard is an input anywhere.
- **Maximum freedom & input.** You can draw literally anything, and *every* stroke becomes a
  creature — so freedom of expression is the mechanic, not a feature.
- **Hidden hand, no hints.** It presents as a sincere doodle toy. The turn is discovered, never
  announced.

## 1. Duck Amuck, inverted (the research spine)

Duck Amuck (Chuck Jones, 1953) is the one ancestor in the research where an unseen animator
torments a *drawn* character, ablating its world one channel at a time, then is revealed to be
another character. Doodle Pad hands the player the animator's role — you draw, you erase, you fling
— and then slowly **gives the drawings a say**, and finally turns the frame around: *you* are a
mark on a larger pad, and another hand is drawing *you*. Metalepsis (A1), enacted, never cited (B4).

## 2. The toy first (the DDLC / juice rule)

- **Papers:** A1 §6.4, A3 §5.1, B2 beat 1, B5 §1.6.
- Every finished stroke is baked to a sprite, classified (blob / worm / dot / fuzz) and given a
  **soul**: googly eyes with spring-lag pupils that overshoot when the body accelerates, idle
  wobble + breathing, a drop shadow, squash/stretch, gravity + floor bounce, hop locomotion,
  ducklings (they follow the cursor), and a wordless reaction-FX kit (hearts, `!`, `?`, `zzz`,
  dust). **Hue silently drives temperament** (red hot, blue sleepy, green social, yellow bouncy) —
  a rule the player *infers*, which secretly plants "these have inner states."
- **First-breath is guaranteed** (critique fix #3): the first stroke always gets the full adorable
  treatment regardless of geometry, so the gasp is never wasted. A resting **bait** doodle
  demonstrates aliveness on load with zero text (critique fix #4).

## 3. The pointer verb set (no typing)

- **Papers:** B1 (teach in seconds, cliché-as-tutorial), input-lens of the design workflow.
- Draw = drag on empty; **grab & fling** = drag on a creature (dizzy spiral recovery); **poke** =
  tap a creature; **seed** = tap empty; **color / eraser** = tap the spilled tray (eraser is a
  *selected tool*, not a gesture — critique fix #1, which also removes the sleep-vs-erase
  collision); **undo** = tap the dog-ear. Everything has a single-pointer path; nothing needs a
  keyboard, hover, or right-click. Hit areas are radius-padded (≥~24–44px).

## 4. The escalation (agency scalar + persisted ledger; no hints)

- **Papers:** A2 (refusal/normalization), A5 (DARVO, but tender), B3 (loop/relation), B2 (subtle
  hint → unambiguous confirmation). Ledger persists in `localStorage` `doodle.v1`.
- **1 Toy** → **2 Will**: bring the eraser near a creature and it flees, corners, covers its eyes;
  spare it and it follows you like a puppy. Only erasing an **alive, fleeing** creature counts as
  cruelty (`erasedAlive`) — correcting a settled doodle is neutral (critique fix #2, the sharpest
  ethics bug). **3 The pad draws back**: on an idle lull, a stroke lays *itself* in, point by point,
  in your palette (`genPadStroke`), then becomes a creature; the first unprompted mark is a *heart*
  above a critter — sweet, which disarms the pre-braced player far better than a scare (critique
  fix #5). **4 The mimic**: a creature copies your last shape, slightly wrong. **5 The other hand**:
  a second, heavier cursor draws on your side and gently ablates channels (desaturate / "tidies"
  your wobble) — always restored within seconds, never a fake crash. **6 The inversion**: the camera
  pulls back to reveal your pad is one small sheet among thousands on a vast pad, a giant pencil
  paused above; your cursor gains a shadow and eyes — you are a mark now — and flinches from the big
  eraser exactly as the creatures did in stage 2. All triggers are **action + soft time floor**, so
  both the frantic scribbler and the careful drawer reach every beat.

## 5. Endings (pointer only, chosen by action + ledger)

- **Papers:** A1 T10, A5 §3.6 / impl. 8 (consent transforms it), B3 §4 (escape = relation).
- **Merge** (gentle default): do nothing near your creatures and they gather to your mark, all eyes
  turn outward together, hearts rise. Warm, no cost.
- **Let it go** (the one consensual real cost): the giant hand *sets down* its eraser beside you;
  pick it up and make a **slow, deliberate 2-second hold-drag** — this genuinely clears the game's
  own `localStorage` (a scar remains). The creatures give a farewell hop and dissolve; the page goes
  blank. The consent is gestural and impossible to trigger by accident (verified) — drawing is
  disabled once you are a mark.
- **Accountability**: if you rubbed out many fleeing creatures, the merge is never offered and the
  farewell has no wave — you feel, from the inside, what you taught them.

## 6. Rails (hidden) & accessibility

- The lie is only about authorship/meaning, never data. Only `doodle.*` localStorage is touched,
  only via the consensual hold-drag; wrapped in try/catch for private mode. No fake browser/OS
  crash. **`prefers-reduced-motion`** damps wobble/breath and the camera move; **no strobing, no
  full-canvas flashes**. DPR capped at 2; awake souls capped at ~36 (rest sleep); creature
  separation prevents piling. Pointer-only, no keyboard/hover/right-click required.

## 7. Data & rendering model

Retained-mode `Stroke` objects (`author` field is invisible to the renderer — the load-bearing
secret that the pad's marks use your exact tools). Velocity→width ribbon via capsule stamping;
each alive stroke baked to an offscreen sprite blitted per frame with a transform; faces/FX drawn
on top; a global view matrix drives the zoom-out; the vast backdrop is one pre-baked texture.
`window.__dbg()` exposes state under `?fast` (a dev accelerator).

## What it deliberately is *not*

No typing, no on-screen text, no menus/score/timer/levels, no rich art tools (freedom is in what
marks *do*, not Photoshop features), no horror (the uncanny comes from tenderness and recognition,
never menace).
