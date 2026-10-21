---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Enable date editing
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Edit dates to enabled.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Edit dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#timeline
- kind: doc
  role: intent
  target: docs/guide.md
---

# Turn on Edit dates

## Trigger

The user turns on Edit dates in the Timeline or a Calendar time grid.

## Outcome

Eligible spans and points can be moved and resized in both views, and the switch is remembered for this graph on this device.
