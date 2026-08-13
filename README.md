# CARET

A small, quiet place to practice your typing.

Type the line that's shown. Watch your words-per-minute climb. Come back tomorrow and keep your streak. There's a **history** link if you want to see how you're doing.

That's all it is.

```
open index.html in any modern browser
```

No install, no account, no network. Everything it knows about you stays on your own machine, in this one browser, and you can wipe it whenever you like.

---

<details>
<summary><strong>Notes for whoever is reading the source (spoilers)</strong></summary>

CARET is a metafiction built in the tradition catalogued in the LAYERS research notes
(`docs/research/notes/` in the sibling `12code4/layers` repo). It does **not** reproduce
LAYERS — no nested arcade, no Custodian, no genre-shifting. It keeps a single surface (a
typing tester) and lets the *content you are made to type* do the work.

The design brief from the prompt was strict: **be innovative, stay easily explorable, hide
your hand entirely, give the player no hints.** So CARET never announces itself as anything
but a typing tool. There is no title card that winks, no "this game will mess with you"
warning, no tutorial pointing at the seams. The player finds the evidence by pulling at it.

The two mechanics it leans on are the ones the research flagged as the most under-used and
the most browser-native:

1. **Behavioral profiling voiced back** (Psycho Mantis, per note A3/A4). Typing is the richest
   possible profiling surface: cadence, error position, self-correction rate, the exact word
   you slowed before, the hour you show up. CARET measures all of it from your real keystrokes
   and, later, reads it back to you. Nothing it says about you is invented.

2. **Complicity through performance** (Spec Ops / BioShock, per A1/A4; "enact, don't cite",
   per B4). A typing tester makes you transcribe. So the voice's lines *become your own
   keystrokes* — you type "i type the words that are put in front of me" in your own hand.
   You can't disown what you typed yourself.

The one instrument that never lies is the **history** panel. Every gaslighting line ("your
first time, isn't it?" — said on your *fourth* session) can be checked against it. That honest
ground is what keeps the deception a spectacle instead of an injury (A5).

It reaches past the tab exactly once, honestly: near the end it offers to hand you the record it
kept of you as a real downloaded file, and then — only with your typed consent — genuinely erases
itself. Nothing else it does touches anything but its own saved data.

See [`DESIGN.md`](./DESIGN.md) for the full mechanic-by-mechanic mapping to the research.

**Ethics rails, kept but hidden** (A5): the only real data it ever touches is its own
`localStorage`, and it only erases that with your explicit, typed consent. No fake browser
crashes, no impersonated OS dialogs, no strobing (reduced-motion is honored). The lie is
always catchable; the machinery never harms the machine.
</details>
