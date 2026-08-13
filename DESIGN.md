# CARET — design notes

> A typing tool that keeps its face straight.
> Built from the LAYERS research corpus, but not from the LAYERS design.

This document maps CARET's mechanics to the research notes (`a1`–`b5`). It is for readers of
the source, not players. **Players get none of this** — that is the entire point.

---

## 0. The brief, and the one decision everything hangs on

The prompt asked for a game that is *innovative, unfamiliar, easily explorable*, that *hides
its hand entirely* and *gives the player no hints* — they "pull at the seams to find the
evidence themselves."

The LAYERS notes repeatedly warn about the **expectation arms race** (A1 §5.1, A3 §4, B1 §5):
post-DDLC audiences arrive *pre-braced* for "one of those games." The moment a metafiction
looks like a metafiction, its hand is already shown. Frog Fractions hid inside another game;
Pirandello flopped in Rome and hit in Milan on expectation alone.

**CARET's answer: don't look like a game at all.** It presents as a mundane utility — a
typing-practice tool. No genre signals, no narrative frame, no wink. A player has no "meta
game" schema to apply, so the hand stays hidden by construction. This is the freshest move the
corpus leaves open, and it's why CARET is a *typing tester* and not an arcade.

The core verb is **typing**, chosen because it uniquely delivers the two tricks the research
calls most under-used and most browser-feasible (below).

---

## 1. The sincere shell (the DDLC / Cookie Clicker rule)

- **Papers:** A1 §6.4, A3 §5.1, B1 impl. 1, B2 beat 1, B5 §1.5–1.6.
- **In CARET:** Phase 0 is a real, quiet, pleasant typing tester — pangrams, honest quotes,
  crisp per-character feedback, a live WPM/accuracy/streak readout, a soft ke/click. It is
  meant to be genuinely usable. The corpus is unanimous: *the shell must be a competent thing
  on its own* or the turn has no floor to fall from (Evoland's 30-minute novelty collapse,
  B5 §1.1). CARET is playtestable "as if the secret didn't exist."

## 2. Behavioral profiling, voiced back (the Psycho Mantis trick)

- **Papers:** A3 §2 (precursors) + §4 "Behavioral profiling voiced back … fully browser-feasible
  and underused"; A4 impl. "Make the Skinner box literal, then let it leak."
- **In CARET:** every keystroke is timed. The app tracks WPM, accuracy, backspace/self-correction
  rate, the **exact word you paused longest before**, the hour of day, and how long you were away
  between sessions. Phase 1 reads these back as flat observations
  (`You slow down before "…"`). It lands because it is **true** — measured, not scripted.
  This is the corpus's "denial + specificity = menace / observation + accuracy = the scare"
  (A2 §GLaDOS rule; A4 Spec Ops lesson: only cite behavior that really happened).

## 3. Complicity through transcription (enact, don't cite)

- **Papers:** A1 T7 (complicity traps), A4 §6 (Spec Ops), B4 §0 + impl. 1 ("enact, never cite";
  SOMA/Disco Elysium success vs. Witness/Everything failure).
- **In CARET:** a typing tester's contract is *transcribe exactly what is shown*. So from Phase 2
  the shown lines become the voice's own words — `i type the words that are put in front of me` —
  and the player **types them, about themselves, in their own hand.** The philosophy is
  performed, never lectured. No philosopher is named; no line explains itself.

## 4. The honest instrument vs. the lying voice (the fair-play / safety rule)

- **Papers:** A5 §2 (the safety valve — the player always has out-of-fiction ground truth),
  §3.1 (Fight Club/Shutter Island retro-auditability), impl. 2 ("the world must be honest so the
  narrator can lie"); B2 impl. 5.
- **In CARET:** the **history** panel is sacred honest ground (A5 impl.: "the settings menu is
  sacred; the one surface that never lies"). Sessions, keystroke totals, first-seen timestamp,
  streak — all real, all always inspectable. Every gaslight the voice tells in Phase 3 is
  **checkable against it within seconds.** That is what converts the lie from injury into
  spectacle, and it is the game's built-in ethical inoculation.

## 5. The gaslighting arc (DARVO, denial-with-specificity)

- **Papers:** A2 §4 (refusal/normalization narrators; GLaDOS "Chapter 2. As always."),
  A5 §1.3 (DARVO: Deny → Attack → Reverse), B3 §3.3 (hold one channel constant while others drift).
- **In CARET:** Phase 3 stages a **fake restart** — cheerful "new session / warm-up," the opening
  pangram again — while the voice insists *"your first time. as always."* The tell is textbook
  B3: the voice's script is serene and near-verbatim while the instruments drift (streak and
  keystroke totals keep climbing; the pangram mutates one word per lap:
  *jumps over the lazy dog → the same dog → does not jump anymore*). Denial is **specific**, so it
  reads as *watching*, not as broken content.

## 6. Escape = refusal, never dexterity (the samsara / Save the Date rule)

- **Papers:** B3 §4 (escape conditions; Twelve Minutes anti-pattern), B4 impl. 4 (Nagarjuna:
  "the new kind of break is always a refusal"), B2 (subtle hint / unambiguous confirmation).
- **In CARET:** the Phase 3 loop is exited by **ceasing to comply** — stop typing. Fourteen seconds
  of stillness and the voice drops its script (`you stopped.`). No timing, no combo; the exit is a
  relation to the loop, not a skill check. A player who keeps obeying still escapes: the loop is
  scripted to crack on its own after three laps (the Stanley Parable Confusion-Ending rule — the
  loop was on someone's schedule), so the arc never softlocks the obedient.

## 7. The strange loop reveal (Hofstadter, enacted)

- **Papers:** B4 §6 (strange loops / tangled hierarchy), A4 §7 (Turing Test inversion — you were
  the apparatus), B2 (pattern→anomaly→hypothesis→confirmation).
- **In CARET:** Phase 4 reveals the passages *were the record* — and the line you are transcribing
  right now describes you transcribing it (`the subject is reading this line … recognition likely`).
  "Practice" was **production**; the typist was the instrument generating the logs (Turing
  inversion). The tangle closes on the last log line: *"i am not the thing that watches you. i am
  the part of you that types what it is told."*

## 8. One real, consensual cost (the NieR Ending E rule)

- **Papers:** A1 T10 (real-stakes sacrifice, once, at the end), A5 §3.6 + impl. 8 ("consent
  transforms assault into sacrament"), A3 impl. 8 (reserve one sincere use of the machinery).
- **In CARET:** the ending is a genuine choice. **Stay** — the app hands you an endless, gentle
  practice that now reads differently (Void Stranger recontextualization; Camus/Hades "staying is a
  real, textured option"). **Release** — the voice first offers to hand you the record (the file
  leak; you `keep` it or let it go), then you type `erase` and the app *actually* clears its record
  of you (only its own `localStorage`), with explicit typed consent, unrecoverable. Every fake
  persistence in the preceding phases is what earns this one real deletion. A tiny scar is left
  behind (OneShot), so a "fresh" start is never quite fresh.

## 9. Browser-native meta, kept safe (the fidelity + rails rules)

- **Papers:** A3 §4 (what a browser can/can't do), B5 §2, A5 §5 (ethics rails).
- **In CARET:**
  - **Cross-session memory** via `localStorage` — the instrument remembers what the voice denies.
    On a *returning* session the app stages a fresh-looking "new session / warm-up" and the voice
    says *"welcome. your first time, isn't it?"* while the history panel shows the real session
    count and keystroke total. The strongest form of the memory battleground (A3 §6, B5 §1.5).
  - **The file leak** (A3 §4 "the browser's one honest IMSCARED move"; B5 §2.3, flagship). At the
    release, the game offers to hand you the record it kept — a real `caret_record.txt` written to
    your Downloads via `Blob` + `<a download>` (no permission prompt). In a sandboxed viewer where
    downloads are blocked, it degrades to showing the text on-screen. The one honest reach past the
    tab, and the reason the erase that follows means something.
  - **Tab title / favicon** — while the tab is hidden (Page Visibility API) the title becomes
    `still there?` / `{name}?`; on return, *"you left. i waited."* The game ran in your absence.
  - **Multi-tab awareness** via `BroadcastChannel` — open a second tab and, once you're past the
    stranger phase, *"there are two of you now. the record has room for one."* (A3 §4 multi-tab).
  - **URL drift** via `history.replaceState` (hash only, so it never reloads and never throws on
    `file://`) — the address quietly deepens `#session → #transcription → #observation`. Deniable
    seam for anyone who watches the bar (A3 §4).
  - **Favicon** is a caret, drawn to a data-URI (no external asset; CSP-safe). **Audio** unlocks on
    first gesture (autoplay policy), done invisibly so the shell stays plain.
  - **A scar** survives erasure (`caret.scar`), so a "fresh" record after deletion is greeted with
    *"have we met? your hands seem familiar."* (OneShot).
  - **Deliberately NOT used:** fake browser/OS crash chrome (the Pony Island "Win7 dialog" trap,
    A3 §2 / A5 §5 — impersonating real chrome is brittle and shades into phishing), real
    notifications (read as spam, A3/B5), and anything that touches data other than CARET's own.
  - **Reduced motion honored;** no strobing (A5 §5 photosensitivity rule). The only "malfunction"
    aesthetic is a one-notch-off chromatic drift, gentle and self-resolving.

## 10. Pacing (Minit / WarioWare / Outer Wilds hook)

- **Papers:** B3 §5 (loop pacing, ≤2–3 dry circuits), B2 §7 (Outer Wilds authored first hook),
  B1 §2 (teach fast).
- **In CARET:** gates are keystroke/beat-count based, not wall-clock, so a fast typist reaches the
  first crack in ~4 lines (~1–2 min) and never waits. The loop is exactly three short laps + a
  break — inside the corpus's tolerance before repetition reads as padding.

---

## What CARET deliberately does *not* borrow from LAYERS

To stay a distinct game rather than a reskin: no nested layers / genre-shifts, no separate
Custodian-and-Observer cast (CARET fuses them into one voice that is, in the end, *the player's own
obedient part*), no arcade/Skinner-dot loop (the compulsion is the WPM/streak of the typing tester
itself), and no live-service update roadmap. CARET is one surface, one sitting, one arc, one honest
instrument, and one real choice.

---

## File map

- `index.html` — the whole game (self-contained; vanilla JS, no dependencies, no network).
- `README.md` — the product face + a spoiler-gated summary.
- `DESIGN.md` — this document.
