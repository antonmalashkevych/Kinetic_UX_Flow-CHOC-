# Kinetic Ana - Iteration 2

Second iteration of the Ana unified chat prototype, driven by the "Kinetic: features that make the rigor visible" proposal (2026-10-20).

## Contents

- `index.html` - v1 prototype baseline (chat-first Option 1 on the Kinetic/CHOC shell), the starting point for v2 changes
- `docs/WOW-GAP-ANALYSIS.md` - item-by-item comparison of the WOW features doc against the current prototype, with recommended options and v2 scope in priority order
- `docs/UX-REVIEW.md` - full-app UX review with severity-rated findings and a fix order

## v2 scope (from the gap analysis)

1. Run card substance + end states (per-step substance, live detail, rejected-archetype chips, Done counts, Needs-you, Honest stop)
2. Answer-to-source lineage panel (figure click opens the chain in the right canvas)
3. Dialog / learn flow (correction, "You taught Kinetic a term", propose-for-organization)
4. Anomaly feed as the home empty state
5. Coverage grid as Cerebrum's Data coverage tab content
6. Finding to playbook to worklist (mocked single motion)

v1 reference repo: github.com/antonmalashkevych/Kinetic_UX_Flow-CHOC-

## Failure states (demo device)
Type a request containing "error" for the data-mart failure card, or "timeout" for the partial-result card. Retry always succeeds.

## Demo triggers (typed into the composer)
- "error": data-mart failure card. "timeout": partial result. "forecast" / "predict" / "next quarter": governed refusal (honest stop).
- "high risk": Needs-you question with candidate buttons (or type your own definition), then the "You taught Kinetic a term" card with Propose for organization.
- Click any bold figure in an answer to open its lineage in the right canvas. Retry and Regenerate skip the triggers.
