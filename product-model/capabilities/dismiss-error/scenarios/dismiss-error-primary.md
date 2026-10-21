---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Dismiss the message
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state clears the Error.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: doc
  role: intent
  target: docs/guide.md
---

# Dismiss an error

## Trigger

A load or write error is shown.

## Outcome

The message is gone; the view and the graph are unchanged.
