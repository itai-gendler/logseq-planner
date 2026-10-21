---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Resize the Node span
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Dates
    - Span
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Write and confirm the selected Node date
  kind: product
  entities:
  - entity: node
    effect: changes
    facts:
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/date-edit.ts#dateChanges
- kind: code
  role: implementation
  target: src/core/timeline-layout.ts#clampDelta
- kind: code
  role: implementation
  target: src/core/calendar-layout.ts#gridDelta
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change one end of a span

## Trigger

Edit dates is enabled and a node has an editable span.

## Outcome

Only the selected end changes and is confirmed in the graph.

## Edge cases

- The start cannot pass the end; Calendar time-grid spans retain at least 15 minutes.
- A Timeline edge clipped outside the range cannot be resized at that edge.
- A one-date point moves but does not resize.
- A failed write reports its reason and reloads the graph; cancellation writes nothing.
