# Ana Unified Chat - Option 1 Prototype

Interactive prototype of the chat-first ("Ana-first") unified chat flow for VQ8 apps, built on an exact replica of the Kinetic v2 shell (CHOC tenant): real logo, Lucide icon set, extracted design tokens, and page wording.

## What it demonstrates

- Ana as its own entity: full-screen chat home (New chat), chat always on the left
- Ask Ana button in every page header + Cmd+J: docked chat panel on the left of any page (Analytical library, Cerebrum, Agents), with the page attached as a removable context chip
- Expand panel to full screen and dock back without losing the thread; one conversation store across all surfaces
- Kinetic-style run card: one-line step indicator (Step N of 7) with Show details accordion, 7-segment progress bar, skeleton placeholders while running
- Finished answer card: Derivation/Operands sections, Grounding and Provenance rows, action bar (Open as report, Create dashboard, Add to library, Subscribe, Pin, Run log, How I got here)
- Artifact canvas: Open as report / Create dashboard opens a Report or Dashboard on the right, chat stays left; from a docked panel it promotes to the full-screen split
- Type Mode popup (Auto / Agentic), ChatGPT/Claude-style stop button, composer autofocus after a reply

## Running it

Open `index.html` in a browser. Single self-contained file, no build step, no network calls (fonts come from Google Fonts).

`ana-unified-chat.html` is the same file; `index.html` is kept as the entry point for GitHub Pages style hosting.

All data is mocked. Answers are canned (A/R over 90 days and denied-dollars scenarios). No PHI; figures are synthetic aggregates.
