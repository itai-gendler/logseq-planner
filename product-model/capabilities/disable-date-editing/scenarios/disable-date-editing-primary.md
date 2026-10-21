---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Disable date editing
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Edit dates to disabled.
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

# Turn off Edit dates

## Trigger

The user turns off Edit dates.

## Outcome

Spans and points in the Timeline and the time grids can no longer be dragged; day and When moves still work.
