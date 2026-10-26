# Gap analysis: "Kinetic: features that make the rigor visible" vs current prototype

Source: Kinetic_Wow_Features_Recommendations (2026-10-20, proposal). Baseline: Ana Unified Chat Option 1 prototype (chat-first on the Kinetic/CHOC shell, repo Kinetic_UX_Flow-CHOC-).

Scoring: Done = in the prototype today. Partial = the frame exists, substance missing. Missing = not represented.

## Item 1 - Query status redesign

| WOW doc requirement | Prototype status |
|---|---|
| Three-layer card: header, progress strip, trace | Done |
| Header: K mark, plain-language statement, elapsed time, Stop | Partial. Statement uses the archetype name ("is working on Derive a measure..."), not a plain-language task ("is explaining the September denial change"). Stop moved to the composer (ChatGPT/Claude style), which supersedes the header Stop and is the better pattern |
| Seven-segment strip + "Step N of 7" one line, never wraps | Done |
| Trace: completed steps show check, elapsed time, one line of substance | Partial. Substance exists for steps 1, 2 and 5 only; steps 3, 4, 6, 7 are bare labels |
| Current step accented with live detail (term resolutions landing) | Missing. Current step shows a static sub-line |
| Rejected archetype alternatives as confidence chips | Missing |
| No percentage, no time-remaining estimate | Done |
| Done state: one-line collapse with time, archetype, counts (metrics, findings, playbooks), reopen trace | Partial. Collapses to "Done + time + Show details"; no archetype or counts in the line |
| Needs-you state: strip stops at amber step, specific question, candidate answers as buttons | Missing |
| Honest stop: refusal with reason and a path forward (request coverage / ask something answerable) | Missing. Only user-initiated Stop exists |
| Trace persists after the answer renders | Done |

**Verdict:** the prototype already made the doc's decision 4 for them - the redesign is in the UI. What is missing is the substance layer and the two non-happy-path end states, which carry the "honest" part of the story.

## Item 2 - Answer to source lineage

Missing. The prototype has static Grounding and Provenance rows and a Source data block in the report canvas, but figures in answers are not controls and there is no lineage chain view.

**Recommended option:** make every bold figure in an answer a control; click opens a lineage panel in the right canvas slot (consistent with the chat-left / artifacts-right rule). Chain: metric identity, definition variant (base vs client VARIANT_OF), surface + isPrimarySurface, period and date basis, query stats, knowledge provenance. This is the cheapest of the big wow items to mock because the canvas infrastructure already exists.

## Item 3 - Dialog mode: ask, offer, learn

Missing. No needs-input question flow, no candidate buttons, no mid-conversation correction, no "You taught Kinetic a term" card.

**Recommended option:** build together with the Needs-you and Honest-stop end states of item 1 as one storyline (refuse, ask, learn). The "taught a term" card with "Propose for organization" renders the AI-proposes-humans-publish ruling and is a strong demo beat; session-scoped by default, explicit proposal action.

## Item 4 - What Kinetic knows about your organization

Missing as a page. Important fit note: production Cerebrum already has a **Data coverage** tab. Recommend implementing this item as the content of that tab rather than a new nav destination - zero navigation change, which respects the CTO's no-major-changes constraint. Coverage grid (metric family x surface: governed / partial / not yet), counts, plain-language change timeline.

On the open decision (show gaps to clients): agree with the doc's recommendation to show them. In RCM, hiding non-coverage is the trust-killer; the gap cells are also the services conversation.

## Item 5 - Finding to playbook to worklist

Missing. Biggest build in the doc, but a mocked version is feasible: a finding card inside the denied-dollars answer, the playbook it unlocks with Kinetic-preparable steps marked, and a draft worklist opening as a canvas artifact (reuses the existing canvas slot), with assignee, cadence, and the "account keys only, no PHI here" line.

## Item 6 - Items without mockups

| Item | Status | Recommendation |
|---|---|---|
| Living anomaly feed as empty state | Partial (home has starters + "Pick up where you left off") | Add "Since you last signed in" with 2-3 anomaly cards, each with one-click "Explain this" that sends the prompt. Cheap, high value, makes the home feel alive |
| Compare two runs side by side | Missing | Skip in v2; needs a second period of mock data to be honest |
| Executive briefing deliverable | Missing | Out of scope (blocked upstream per the doc) |
| Ana voice | Missing | Out of scope for the prototype |
| What-if on governed metrics | Missing | Hold per the doc; agree it is the credibility risk |

## Recommended v2 scope (priority order)

1. **Run card substance + end states** (item 1 gaps): per-step substance lines, live detail on the current step, rejected-archetype chips, Done line with counts, Needs-you with candidate buttons, Honest stop with reason and actions. Smallest effort, completes the existing centerpiece.
2. **Lineage panel** (item 2): figure-click to canvas lineage. The doc's own demo sequence opens with it.
3. **Dialog / learn flow** (item 3): correction + "taught a term" card, chained to Needs-you.
4. **Anomaly feed on home** (item 6a).
5. **Coverage tab content** (item 4) - static grid, one screen.
6. **Finding to worklist** (item 5) - mock the three-step motion with one canned finding.

This covers the doc's full demo sequence (lineage; honest stop + dialog; finding to worklist) inside the existing prototype architecture.

## Positions on the doc's open decisions

1. Demo audience: not mine to call, but the v2 scope above supports all three audiences; investor emphasis = 2 + 5 (item 4), client emphasis = 1 + 3 + 5.
2. Rejected archetypes with confidence: show them, but only inside the expanded trace (not the collapsed line), which contains the risk the doc worries about - an odd score is visible only to a user who asked to see the reasoning.
3. Coverage gaps to clients: show.
4. Query status redesign into the current UI/UX artifact: already done in the prototype; adopt.
