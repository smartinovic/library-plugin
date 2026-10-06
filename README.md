# library — a Claude plugin

Your personal reading library in Claude, for readers invited to it: a librarian who knows your
shelves, a ritual for finishing a book, honest queue triage, film and series picks that never spoil a
book you haven't read, and taste tuning measured on your own ratings.

It is one remote connector plus five skills:

| skill | what it does |
|---|---|
| `librarian` | ranks your next reads, discovers books in two lanes (in your wheelhouse · out of the blue), more like a book you loved, a subject ladder |
| `finish` | records a finished (or rejected) book — rating, date, a one-line verdict, passages — and checks the verdict against your taste |
| `tbr-triage` | walks your queue, the books that fit you least first, in batches of five |
| `projectionist` | films and series from your book taste and your screen log — never an adaptation of a book you haven't finished |
| `taste-tuner` | turns a complaint about your recommendations into one measured change, kept or dropped on the evidence |

This repository holds no data. Your library lives on its own server; the connector reads and changes
it only for you, after you sign in with your passkey and allow it.

## Install

**claude.ai (web, desktop, phone):** Customize → Plugins → Add marketplace → `smartinovic/library-plugin`,
then install **library**. Open the plugin's Connectors tab and connect: you'll be sent to the library to
sign in with your passkey and allow Claude. The skills then work in any Claude app, your phone included.

**Claude Code:**

```
/plugin marketplace add smartinovic/library-plugin
/plugin install library@library
```

The first tool call opens the library's sign-in in your browser.

## Using it

Ask naturally — "what should I read next?", "I finished the book", "let's clean up my queue", "what
should we watch tonight?" — or call a skill by name: `/library:librarian`.

To disconnect: Account → Connected apps → Remove, on the library itself.

Only readers invited to the library can sign in.
