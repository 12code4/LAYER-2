# LAYER-2

Small browser games in the metafiction / frame-breaking tradition — each built from the
research notes in the sibling `12code4/layers` repo (`docs/research/notes`), each a sincere,
mundane-looking tool that hides its hand and lets the player pull at the seams. No warnings,
no tutorials, no hints. Every one is a single self-contained HTML file: vanilla JS, no
dependencies, no network, nothing leaves your machine.

## The games

### `index.html` — **CARET**
A quiet typing-practice tool that reads you back from your own keystrokes, then begins to
gaslight you about your own history — until you realize the passages *were* the record and you
were producing it. Complicity through transcription; the honest "history" panel never lies.
Ends on a real, consensual choice. → design: [`DESIGN.md`](./DESIGN.md)

### `doodle/index.html` — **Doodle Pad**
Pointer only, no keyboard. You draw freehand and every scribble comes alive — googly eyes,
physics, ducklings that follow your cursor. It's a genuinely fun toy... and then it starts
drawing *back*. A creature mimics your last shape; a second hand appears; the camera pulls back
to reveal your whole pad is one doodle on a vast pad, your own cursor now a mark among the
critters. Duck Amuck, inverted. → design: [`doodle/DESIGN.md`](./doodle/DESIGN.md)

```
open either index.html in any modern browser — that's it
```

## Shared principles

- **Hide the hand.** Each looks like an unremarkable everyday tool. The freshest move in a
  post-DDLC world is to not look like a game at all.
- **No hints.** Seams are discoverable by ordinary curiosity; confirmations are unambiguous.
- **The lie is catchable and never harmful.** Deception is about *meaning*, never data. The only
  real destruction is a consensual one the player chooses; no fake crashes, no strobing;
  `prefers-reduced-motion` honored.
- **Enact, don't cite.** The idea is delivered through what you *do*, never through on-screen
  essays.

Design for each game was developed with research reading and, for Doodle Pad, a multi-agent
design + adversarial-critique workflow. See the per-game `DESIGN.md` files for the full
mechanic-by-mechanic mapping (spoilers).

_A third prototype (a typing sandbox) was cut when the brief moved to "no typing."_
