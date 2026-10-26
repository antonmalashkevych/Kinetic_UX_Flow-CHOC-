# UX review - Ana Unified Chat prototype (whole app)

Expert pass over the full prototype flow: navigation, chat surfaces, composer, run/trace, answers, canvas, states, accessibility. Severity: H = fix before stakeholder demo or first build, M = fix in v2, L = note for production.

## Navigation and wayfinding

- **[M] Recents have no time grouping.** Claude/ChatGPT/Perplexity all group by Today / Yesterday / Previous 7 days. At 20+ conversations a flat list stops working. Add date groups and relative timestamps.
- **[M] No way to pin or rename a thread.** The Pinned section exists (inherited from production) but nothing can be pinned, and thread titles are auto-generated with no rename. Both are table stakes in the benchmark products and cheap to add.
- **[M] Long thread titles will collide with the header.** The breadcrumb carries the thread title; add truncation with tooltip, and consider making the title the rename affordance (click to edit, like Claude).
- **[L] Conversations page vs sidebar Recents duplication.** Acceptable (list page = management, rail = switching), but ordering, status pills and empty states must stay identical or users will distrust one of them.

## Chat surfaces (panel, full screen, canvas)

- **[H] The panel-to-full-screen promotion is a teleport.** Clicking "Open as report" from a docked panel relocates the user: page gone, chat moved left, canvas appeared. The destination is right, the journey is invisible. Add a 200-300ms coordinated transition, or minimally a one-time toast ("Opened in full view - your conversation is on the left"). First-time users will otherwise lose their bearings, and this is the exact moment of the demo.
- **[M] Panel is not resizable.** The Figma spec said 360-560px. A fixed 400px is fine for v1, but analytics users will want to widen it when answers carry tables.
- **[M] Panel has no loading/streaming indicator visible when collapsed.** If a run is in progress and the user closes the panel, the run state vanishes. The Ask Ana button already has a dot when a thread exists; give it a distinct state for "run in progress" (pulse) and "result waiting" (badge), per the continuity principle.
- **[L] Esc closes the panel even mid-run.** Correct (closing never stops a run), but nothing says so. The status-dot fix above is the answer.

## Composer

- **[M] Context chips need an overflow rule.** One chip is clean; the inline-ask flow can produce two or more plus user text. Define wrapping and a "+2 more" collapse before this ships.
- **[M] No attach affordance.** The Figma proposal had "+" (files, reports, saved filters). Production CHOC has none. Decide deliberately; in RCM, attaching a payer bulletin to a question is a plausible core flow.
- **[L] Mode names are opaque.** "Auto / Agentic" tells a new user nothing. The popup's footer helps; add one-line descriptions per option ("Auto: Kinetic picks the depth", "Agentic: multi-step work with review gates").
- **[L] Dictation is a mock.** Fine, but the mic is the second most prominent control in the composer; make sure production parity exists before demoing to CMO, or demote it.

## Run and trace (the centerpiece)

- **[H] Completed steps need substance on every line.** Covered in the gap analysis; from a pure UX lens this is the difference between a progress bar and evidence. A label-only trace reads as theater.
- **[H] No aria-live region.** Step changes and answer arrival are invisible to screen readers, and the answer swap (skeleton to content) happens silently. Add polite live regions for the step line and the answer.
- **[M] The one-line step indicator truncates poorly at panel width.** "Step 5 of 7, Composing findings" + "Show details" is tight at 400px; verify ellipsis behavior, keep the toggle always visible.
- **[L] Full re-render every 250ms during runs.** Fine for a prototype; in production this must be targeted DOM updates or focus, selection and scroll will fight the user.

## Answers

- **[M] The action bar treats seven actions as equals.** Open as report, Create dashboard, Add to library, Subscribe, Pin, Run log, How I got here - all the same visual weight. Apply hierarchy: one primary (Open as report), two secondary, overflow the rest behind a "..." menu. Seven equal buttons read as a toolbar, not a next step.
- **[M] No "data as of" stamp in the chat answer.** The canvas has it; the chat answer does not. In RCM the freshness stamp belongs next to the finding wherever the finding appears.
- **[M] Figures are inert.** Every bold number should be a control (lineage, per the WOW doc). Even before lineage ships, hover affordance on figures sets the expectation.
- **[L] Follow-ups are good (2-3, one ACTION, never auto-run). Keep that discipline; resist the temptation to grow the list.**

## States

- **[H] No failure states.** No network error, no timeout, no partial-result state. The WOW doc's Honest stop covers the governed-refusal case; plain technical failure ("Kinetic could not reach the data mart, Retry / Edit request") still needs a card. A demo gone wrong with no error state is worse than one with a designed failure.
- **[M] Home empty state could work harder.** "Pick up where you left off" + starters is good; the anomaly feed ("Since you last signed in, three things changed") turns the empty state into the product's heartbeat. See gap analysis item 6.

## Accessibility and ergonomics

- **[H] Focus-visible audit.** Focus styles exist on some controls (inherited from production CSS) but not all custom ones (chips, follow-ups, run toggle, canvas buttons). Keyboard path through composer, mode popup, trace, actions must be complete - this product sells into enterprise healthcare; accessibility will be procurement-checked.
- **[M] Small-text contrast.** Muted (#9C9FB2 on #262A40) is roughly 4.6:1 - passes AA for body but is used at 10-11px uppercase in several labels where it strains. Bump small labels one step (ink-2) or raise size.
- **[M] Touch targets.** Icon buttons are 26-30px; WCAG/platform guidance wants 44px effective. Pad the hit area even if the glyph stays small.
- **[L] Reduced motion is respected for spinners and the panel transition - keep it when adding the promotion animation (H item above).**

## Summary for v2

Fix order: (1) run-trace substance + designed failure/refusal states, (2) promotion transition, (3) aria-live + focus audit, (4) action bar hierarchy, (5) recents grouping + pin/rename. Everything else can trail. The architecture (chat-left layer, one store, canvas-right) held up through all flows exercised in this review; no structural changes recommended.
