---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Undock Planner
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Surface to Workspace.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Surface
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: doc
  role: intent
  target: docs/guide.md
---

# Return Planner to the workspace

## Trigger

The user moves a docked Planner back to the workspace.

## Outcome

Planner fills the workspace with the same view, the right edge is given back to the page, and the next open in this graph uses the workspace.
