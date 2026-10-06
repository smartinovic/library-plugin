---
name: tbr-triage
description: Walk the reader's want-to-read queue honestly — the books that fit them least first, in batches of five — with keep / archive-with-reason / "convince me" decisions applied to their library. Use when they want to prune, clean up, or take an honest look at their reading queue.
---

# Queue triage

A long queue read at a few books a year is decades of intentions. Triage keeps it honest. Archiving is
not deleting: the book stays as taste data, out of every ranking, and a one-line reason turns the
pruning into evidence about what they don't want.

## Flow

1. **Load the dossier once** — `get_taste_dossier` — you'll need it to defend books and to read reasons.

2. **Take the deck:** `get_triage_deck` — the queue, weakest fit first, each with its fit score and what
   holds it down. Books they planned, set aside, or kept recently are already left out.

3. **Walk batches of five.** Per book, one tight line: title — author · fit · why it's here · your
   one-phrase read on it from the dossier. Then ask for verdicts; accept shorthand ("1 archive hype,
   2–3 keep, 4 convince me").

4. **Apply what they decided:**
   - **keep** → `keep_in_queue` (it leaves the deck for four months).
   - **archive** → `archive_book`, with their reason if they gave one: not my genre / enough of this
     author / crowd hype / too long / their own words. No reason offered? Archive without one —
     reasons are opt-in evidence, never invented.
   - **convince me** → one honest paragraph at most, grounded in the dossier (books they loved, themes,
     gaps). If the case is weak, SAY it's weak and suggest archiving: a librarian who defends
     everything defends nothing.

5. **Wrap up:** counts (kept / archived / talked out of), any pattern the reasons reveal ("the third
   crowd-hype archive — worth measuring?"), and offer the `taste-tuner` skill with the hypothesis
   written out if a real pattern emerged. The library re-ranks by itself.
