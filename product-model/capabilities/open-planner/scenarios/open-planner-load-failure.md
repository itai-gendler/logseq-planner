---
kind: edge
routes:
  main: Planner in Logseq
steps:
- text: Open Planner
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Begin loading Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts: []
    from: Hidden
    to: Loading
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Record the load failure in Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
    from: Loading
    to: Load failed
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openBody
- kind: code
  role: implementation
  target: src/ui/workspace.ts#initialTag
- kind: code
  role: implementation
  target: src/ui-state.ts#createUiStore
- kind: doc
  role: intent
  target: docs/guide.md
---

# Show an initial graph load failure

## Trigger

Loading the graph schema or week-start setting fails.

## Outcome

The error is shown with Retry; the view is not described as an empty graph.
