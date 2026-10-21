---
kind: edge
routes:
  main: Planner in Logseq
steps:
- text: Move the Node dates
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Dates
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Restore earlier Node dates after failure
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
- text: Show the failure in Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/view-area.ts#dateMoveOf
- kind: code
  role: implementation
  target: src/core/when.ts#whenMove
- kind: code
  role: implementation
  target: src/core/date-edit.ts#writeDates
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveDate
- kind: doc
  role: intent
  target: docs/guide.md
---

# Recover a failed date move

## Trigger

A date write or read-back fails.

## Outcome

Earlier confirmed dates are restored where possible, the result is reported, and the view reloads graph values.
