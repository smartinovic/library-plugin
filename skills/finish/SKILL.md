---
name: finish
description: Record that the reader finished (or gave up on) a book in their library — rating, date, a one-line verdict, saved passages — and check the verdict against their taste profile. Use when they say they finished, read, or quit a book.
---

# Finish a book

Finishing is when a reader knows best what a book was to them. Capture it in one light pass — never a
form, never a nag.

## Flow

1. **Find the book.** `search_library` with words from the title — or, if they just say "finished my
   book", `search_library` with `status: ["reading"]` and ask which. Confirm the title and author before
   writing anything.

2. **Gather, conversationally** — all optional:
   - a rating, 0–5 in half stars;
   - when they finished (default today; a year alone is fine for an old read);
   - **the verdict** — one sentence on *why* that rating. If they already said something ("loved it but
     the ending dragged"), distil THAT and confirm it rather than asking again;
   - passages they want to keep, if any come up.

3. **Write it — after they agree:** `log_finish` with the book's id and only what they said. A re-read
   is handled by the library (the earlier read and its rating stay in their history). Each passage:
   `save_quote` with the text and where it is.

   **Quitting instead?** First ask which kind of quit it is:
   - **Rejected it** — gave it a fair chance and it wasn't for them: `log_dnf` with the verdict. The
     engine counts it as their lowest rating; no need to ask for stars.
   - **Set it aside to finish someday** — that is NOT a rejection. Leave it on want-to-read and say so.

4. **Check the verdict against their taste.** Call `get_taste_dossier` and judge honestly:
   - It **confirms** the profile → say so in one line, done.
   - It **contradicts** it — they loved a book in a theme they usually punish, or disliked one the
     engine predicted as a hit → name the theme or signal, quote the verdict as the evidence, and offer
     to *measure* a change with the `taste-tuner` skill. One book tunes; it doesn't overhaul.

5. **Loose ends, one line each, only when true:** it is a series volume (is the next one wanted?); this
   was their first loved book by the author (more by them is worth a look); nothing else.
