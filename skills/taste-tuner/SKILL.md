---
name: taste-tuner
description: A measured tuning session for the reader's fit engine — turn a complaint ("too much of one author", "it never shows me short books") into one falsifiable change, measure it on their own ratings before anything changes, and keep or drop it on the evidence, with the decision written in their taste journal. Use when they want to tune what their fit score weighs or question why the engine ranks something.
---

# Taste tuner

Tuning discipline: every change is measured on the reader's own ratings before it survives, and every
decision is written down — kept or dropped — so the next session never re-tries a dead end.

## Flow

1. **State the hypothesis.** From their words, one falsifiable line — "the crowd's rating is pulling
   popular books up" — and what improving would look like.

2. **Look first.** `get_tuning_lab`: the weights their score uses and their ranges, how many rated books
   there are to measure on (it needs 30), the latest measurement, and the journal. Read the journal —
   don't re-try a measured dead end without new evidence.

3. **Change one knob** (or one tight pair) and `measure_taste_change` with the weights and the
   hypothesis. It changes nothing; it returns:
   - **predicts their ratings** — author-held-out r as it is vs proposed, the paired difference with
     its 90% interval and how often it wins. Judge on the interval, never on the difference alone; a
     move under ~0.005 is the instrument's own floor;
   - **back then** — the chronological replay. When the AUTHOR weight moved, this is the line that
     decides: the author-held-out one removes the author first and always calls that signal useless;
   - **loved vs disliked** — how far apart their scores sit;
   - **follows the crowd** — popularity leakage; past the wire the list ranks by popularity, not by them,
     and the rules stop short of it;
   - **the top 20** — which books would enter and leave. Numbers can hold while the menu changes.

4. **Decide by the rules, with them:** keep only if the interval clears zero, leakage stays inside the
   budget, and the top-20 change makes sense to them. Otherwise drop it. `decide_taste_change` with
   `kept` or `dropped` and a one-line note — the journal keeps it with the numbers either way. A
   reader's keep changes their weights at once; the library owner's weights live in code, so for him a
   keep records the change to make there.

5. **Note the why.** If the session taught something about their taste that isn't a weight — "short
   books aren't a preference, it's that the ones on my list are thin" — `add_journal_note` in their words.
