# Ana Unified Chat - Option 1 Prototype

Interactive prototype of the chat-first ("Ana-first") unified chat flow for VQ8 apps, built on an exact replica of the Kinetic v2 shell (CHOC tenant): real logo, Lucide icon set, extracted design tokens, and page wording.

## What it demonstrates

- Ana as its own entity: full-screen chat home (New chat), chat always on the left
- Ask Ana button in every page header + Cmd+J: docked chat panel on the left of any page (Analytical library, Cerebrum, Agents), with the page attached as a removable context chip
- Expand panel to full screen and dock back without losing the thread; one conversation store across all surfaces
- Kinetic-style run card: one-line step indicator (Step N of 7) with Show details accordion, 7-segment progress bar, skeleton placeholders while running
- Finished answer card: Derivation/Operands sections, Grounding and Provenance rows, action bar (Open as report, Create dashboard, Add to library, Subscribe, Pin)
- Confidence level on every answer: Certified (100%), Governed (70-99%), Assisted (40-69%), Partial data (below 40%, below the acceptable threshold), color coded green / blue / amber / red, with a ? tooltip showing the percentage, the reason, and the tier scale
- Perplexity-style trust layer: inline citation chips (hover shows report, cell and value), thumbs up/down with an optional reason popover (plus "Tell us more" for free-text feedback in the same popover), and an "N sources" pill that opens a Sources pane on the right listing the exact report cell behind each figure. The pane opens with a confidence summary bar, and "Trace in Cerebrum" switches it to a Cerebrum-style Sankey (data product, kind, cited cell) with impulses travelling along each source's ribbon, plus a back arrow to the list
- Artifact canvas: Open as report / Create dashboard opens a Report or Dashboard on the right, chat stays left; from a docked panel it promotes to the full-screen split
- Type Mode popup (Auto / Agentic), ChatGPT/Claude-style stop button, composer autofocus after a reply

## Running it

Open `index.html` in a browser. Single self-contained file, no build step, no network calls (fonts come from Google Fonts).

`ana-unified-chat.html` is the same file; `index.html` is kept as the entry point for GitHub Pages style hosting.

- Data-access gaps stated first: when Kinetic can't read data the question needs (for example CARC/RARC 129 / N770, drugs, submission dates), the answer opens with a red notice naming what is not accessible, offers Request data access / Attach screenshot or file / Paste data, and labels anything below as partial context (try the "Denial Reason Drill-down" starter prompt)

## Cerebrum page

The Kinetic graph tab is the real Cerebrum stage (the cerebrum-canvas drill build), not a mock. It fills everything the page controls leave free: full width from the sidebar to the edge, down to the bottom of the viewport, on its original near-black background.

- Toolbar (Kinetic controls, above the stage): counts, Group by **Lobe / Region / Kind / Scope**, Find, View / Edit, Reset, Full screen.
- Scope groups the same neurons into two hemispheres, the client's (CHOC, learned here) and the global one (shared by every client). Each keeps the lobe arrangement; the tracts between them are the cross-scope synapses. Scope shares per kind are sample values; in production it is each node's own scope field.
- On the stage: breadcrumb, gesture hints, Scenes menu (bottom left), readout (bottom right). Click a lobe, then scroll in, press Enter or double-click to open the data inside (Sankey, node table, neighbours).
- How it is wired: the stage source is inlined as inert text in `#cerebrum-src` and mounted once in an iframe by `cereMount()`, so it keeps running while the page re-renders (Ask Ana docking, tabs). The toolbar talks to it with `postMessage` (`mode`, `edit`, `reset`, `find`); the stage reports `state` (mode, edit, counts) back. Sound is off in this embed.

## Agents (live maps)

The Agents page visualizes existing revenue cycle agents with a live map inspired by lot-map, drawn on the Cerebrum stage (deep radial background, aura nebula, impulses, Cerebrum hues: grounding blue for data, governance amber, agent violet for reasoning, executable orange for outputs). Creating agents moves into chat later, so New agent points to Ana.

- Fleet map (top of My agents, Approvals and Activity): Kinetic core, six agents orbiting, shared stations (Claims, Remittance, Charges, Cerebrum, Skills, Superset, Library, Approvals, You). A running agent sends impulses to the stations it uses; badges show approvals waiting and runs that stopped. Hover for details, click to open the agent. Agents start runs on their own every few seconds.
- Agent map: the agent in the centre with a token-budget ring (amber at 70%, red at 90%), ten stations around it. Impulses fly out when a call starts and return when it ends, spokes thicken with use, a dotted route joins the last stations visited, clock hands grow around a running station, ×N for parallel calls, red dot for errors, a wide ring when the answer is delivered.
- Beside the map: line of now, play/pause, replay, 1×/2×/4× and a scrubber for past runs (live runs show a Live pill), the run feed (● running, · done, ✕ failed, ◆ delivered, +N folded), and the result card with findings, outputs and approvals.
- Runs tab: every run with status, run time, tokens and headline; Replay on map.
- Settings tab: name, instructions, skills, schedule and event triggers, capabilities, approval, delivery (Kinetic, email, Slack), token cap, memory, pause and delete, Test agent with unsaved settings. Capability and skill changes show on the map from the next run.
- Approvals: evidence first (finding, 8-week chart, supporting figures, what approving does), decision at the bottom: Approve, Send change request, Reject, Undo. Approving sends an impulse from Approvals to the agent and on to the target on the fleet map.
- Activity: tokens this month, tokens by agent, all runs across agents with filters and Replay.
- Demo states: Prior auth denial watch shows a run stopped at the token budget (Retry from checkpoint, Raise the cap); Denial driver monitor run #42 and AR Over 90 Share run #9 show partial data gaps.

All data is mocked. Answers are canned (A/R over 90 days and denied-dollars scenarios). No PHI; figures are synthetic aggregates.
