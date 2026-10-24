# Quantum Diagram Design

Adapted from cathrynlavery/diagram-design (GitHub trending, Oct 2026; 45 types, MIT). Security-vetted 2026-10-20: SKILL.md clean, no external calls; references are design docs only. Adapted to this workspace's content and shop work.

## Output

Every diagram is one self-contained HTML file with inline SVG — no external assets, no JavaScript required. It must render correctly opened directly in a phone browser.

Default editorial tokens (customize per brand when the user provides one):

- Paper: #f5f5f5
- Ink: #2d3142
- Accent (focal nodes only): #bf4520

## Philosophy — deletion is the highest-quality move

- Every node is a distinct idea. Two nodes that always travel together are one node.
- Every connection carries information. If the relationship is obvious from layout, remove the line.
- Accent color is editorial, not a flag: 1-2 focal nodes per diagram. On 5 nodes it erases the signal.
- The diagram is done when nothing can be removed, not when everything is added.
- Target density 4/10. Above 9 nodes, it is probably two diagrams.

## Types worth using here

- **Flowchart / process** — order flow (inbox → confirm → pack → courier → COD), tool workflows, setup steps.
- **Timeline / Gantt** — content calendars, 7-day posting plans, application windows (start → deadline).
- **Funnel / pyramid** — reach → inbox → order → delivery conversion; pricing tiers.
- **Bar / dumbbell / waterfall** — price comparisons, before/after metrics, profit build-up (sales − costs = profit).
- **Swimlane** — who does what: page admin vs courier vs customer.
- **Quadrant / radar** — product positioning (price vs demand), channel comparison.
- **Tree / org chart** — product category trees, skill/goal breakdowns.
- **Sankey** — where views go (views → profile visits → inbox → orders), when real numbers exist.

The full 45-type catalogue (architecture, sequence, ER, Wardley, Sankey, fishbone, journey maps and more) is available on request from the source repo's type references.

## Rules for this workspace

- Never draw numbers that were not given or measured. A diagram of imagined metrics is a lie with nicer typography.
- Bangla labels are fine — use a font stack that carries Bangla glyphs; never Bengali font for Latin text.
- One diagram per question. Label the focal node, keep captions outside the SVG as normal text.
- Deliver the HTML file as an attachment or a hosted link the phone can open; verify it renders non-blank before sending.

## Before the first diagram for a new brand

Ask once whether to customize the tokens (brand colors) or keep the editorial defaults. After that, remember the choice in the project files and do not ask again.
