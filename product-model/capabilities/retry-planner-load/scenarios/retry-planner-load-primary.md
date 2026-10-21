---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Retry
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Clear the Error and reload Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Error
    from: Load failed
    to: Loading
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present the loaded Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Displayed data
    from: Loading
    to: Ready
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openBody
- kind: doc
  role: intent
  target: docs/guide.md
---

# Retry the graph load

## Trigger

The initial load failed.

## Outcome

The graph loads and Planner is ready.

## Edge cases

- Another load failure keeps the error and Retry available.
