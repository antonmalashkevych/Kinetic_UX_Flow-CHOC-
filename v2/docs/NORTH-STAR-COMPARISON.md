# v2 prototype vs north star vision and the WOW features doc

Date: 2026-10-26. Baseline: kinetic-ana-v2 at commit c8c6c28.

Assumption: no single file was named "north star", so I used two sources. (A) Your stated concept: chat first and chat always, full screen and docked, chat left and artifacts right, Perplexity/Claude/ChatGPT conventions, one Ana across VQ8 apps, minimal visual change. (B) The Figma "Ana everywhere: one assistant, every VQ8 app" analysis (six recommendations plus the gaps list). If your north star lives elsewhere, send it and I will re-run this.

Scoring: Done, Partial, Missing, or Deliberate (a conscious departure).

## A. Your concept

| Principle | Status | Notes |
|---|---|---|
| Chat first | Done | Ana home is the default landing view; New chat and Search lead the rail |
| Chat always (any page) | Done | Ask Ana in every page header, Cmd+J, docked panel on Library, Cerebrum, Agents |
| Full screen and panel, one thread | Done | Expand and Dock keep the thread; one store feeds Recent, Conversations, Pick up |
| Chat left, artifacts right | Done | Report and Dashboard open in a right canvas; both splitters are resizable |
| Continuity when panel closed | Done | Ask Ana shows running, result waiting, and thread-exists states |
| Perplexity-grade answers | Partial | Numbered citation chips and follow-ups exist. No sources row, no related-question block at the quality Perplexity sets |
| No major visual change (CTO) | Done | Exact CHOC/Kinetic replica. The nav restructure is the one real change, and it is Option 1 only |
| One Ana across all VQ8 apps | Partial | Only Kinetic is built. In-chat identity still says "Kinetic" (see B6) |

## B. Figma "Ana everywhere" recommendations

| # | Recommendation | Status | Gap or note |
|---|---|---|---|
| 1 | One Ana, three surfaces: Home, docked panel, inline Ask Ana on charts, rows, selections | Partial | Home and panel done. Inline Ask Ana on objects is not built (page-level context chip only) |
| 2 | Persistent left rail: New chat, Search, Projects, Library, Scheduled, Recents by date with origin-app tag | Partial | New chat, Search, Conversations, Library, grouped Recents, pin and rename done. Projects, Scheduled and origin-app tag missing |
| 3 | Visible, editable context chips (app, filters, selection, files) | Done | Page, file, report and filter chips, removable, with overflow rule and +N more. App chip waits for a second app |
| 4 | Prose answers with sources: citations, sources row, action bar, charts in side canvas | Partial | Citations and side canvas done. Answers still sit in the production boxed card (Deliberate, for CHOC fidelity). Sources row and message actions (copy, regenerate, helpful, share) missing |
| 5 | Run cards become compact task blocks | Done | One-line step indicator plus accordion, collapsed Done line with time |
| 6 | Kinetic tokens only | Done | Live-extracted tokens. Note: Figma names IBM Plex Sans, CHOC production uses Inter, prototype follows production |

Run-state model from the Figma analysis (Working, Needs input, Review and confirm, Done, Stopped, Failed):

| State | Status |
|---|---|
| Working | Done |
| Done | Done |
| Stopped | Done (composer Stop, ChatGPT style) |
| Failed | Done in v2 (data-mart error card with Retry and Edit request) |
| Partial result | Done in v2 (not in the Figma list, added from the UX review) |
| Needs input | Missing |
| Review and confirm, Undo window, Resume after Stop | Missing |

Figma "gaps vs modern chat UX" that remain: no message actions, no plain-answer thinking state, no Ask / Research / Agent mode switch (prototype has Auto and Agentic), no Projects, no cross-app continuity, no per-app identity cleanup, dead-end destinations (Scheduled).
Closed since v1: single-line composer (now has attach "+", chips, mode, stop), invisible context, conversation history (recents, search, rename, pin), surface count.

## C. WOW features doc ("Kinetic: features that make the rigor visible")

| Item | v1 status | Now | Change |
|---|---|---|---|
| 1. Query status redesign: three-layer card, strip, one line | Done | Done | none |
| 1. Per-step substance lines | Partial (steps 1, 2, 5) | Partial | none yet |
| 1. Live detail on current step, rejected archetype chips | Missing | Missing | none yet |
| 1. Done line with archetype and counts | Partial | Partial | none yet |
| 1. Needs-you state | Missing | Missing | not built |
| 1. Honest stop (refusal with reason and path) | Missing | Partial | Technical failure and partial result built. Governed refusal (coverage gap) not built |
| 2. Lineage: figures become controls, chain in right canvas | Missing | Missing | not built |
| 3. Dialog: ask, offer, learn ("You taught Kinetic a term") | Missing | Missing | not built |
| 4. What Kinetic knows (as Cerebrum Data coverage tab) | Missing | Missing | not built |
| 5. Finding to playbook to worklist | Missing | Missing | not built |
| 6a. Living anomaly feed on empty state | Partial | Done (mock) | "Since you last signed in, three things changed", Explain this, data-as-of stamp. Sits below starters |
| 6b-e. Compare runs, exec briefing, Ana voice, what-if | Missing | Missing | out of scope or on hold per the doc |

Tally against the WOW doc: 2 items Done, 2 Partial, 4 Missing of the six numbered items, plus 6a now closed. The doc's demo sequence (lineage; honest stop plus dialog; finding to worklist) is not yet demoable end to end, because items 2, 3 and 5 are absent.

## D. UX review items (from UX-REVIEW.md)

Closed: recents grouping, pin and rename, title truncation, promotion transition and toast, resizable panel and canvas, collapsed-panel run status, chip overflow, attach, failure states, anomaly feed, loaders.
Open: action bar hierarchy (still seven equal buttons), data-as-of stamp in the chat answer, figures as controls, aria-live regions, focus-visible audit, small-text contrast, 44px touch targets, mode descriptions, dictation honesty.

## E. Where v2 stands, and what I recommend next

Strong: the structural north star (chat-first, always-on, left chat and right artifact, one store, visible context) is essentially complete, and it did so without touching CHOC's look.

Weak: the north star's content layer. The WOW doc is about proving rigor, and the prototype shows the frame of that story but not the proof. The inline Ask Ana, message actions, sources row, and cross-app continuity are the remaining shell gaps.

Recommended order:
1. Run-card substance and Needs-you plus governed refusal (finishes the centerpiece, smallest effort).
2. Lineage panel in the right canvas (opens the doc's demo sequence, reuses the canvas).
3. Dialog and learn flow chained to Needs-you.
4. Message actions and a sources row (cheap, closes the Figma modern-chat gaps).
5. Inline Ask Ana on a chart and a table row (the missing third surface).
6. Action bar hierarchy and the accessibility pass (H items in the UX review).
Defer: Projects, Scheduled, cross-app continuity (need a second app shell), coverage tab and worklist (largest builds).

Decision for you: the north star says one Ana, but the prototype keeps "Kinetic" as the in-chat name for CHOC fidelity. Pick per variant: Option 1 should say Ana, Option 2 can keep Kinetic.

## Update 2026-10-26 (after items 1-4)

Built: (1) run card substance per step, live detail on the current step, rejected-archetype chips in the expanded trace only, Done line with archetype and counts, Needs-you state with candidate buttons, governed refusal; (2) lineage panel in the right canvas from any bold figure; (3) dialog/learn: "You taught Kinetic a term" with Propose for organization and Forget; (4) message actions (copy, regenerate, helpful, not helpful, share) and a sources row.
Still open from the recommended list: inline Ask Ana on objects, action bar hierarchy, accessibility pass, Review and confirm state, coverage tab, finding to worklist.
