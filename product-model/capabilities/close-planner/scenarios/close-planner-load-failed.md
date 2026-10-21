---
kind: alternate
routes:
  main: Planner in Logseq
steps:
- text: Close Planner
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Hide Planner state
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts: []
    from: Load failed
    to: Hidden
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
  target: src/ui/workspace.ts#createWorkspace
- kind: doc
  role: intent
  target: docs/guide.md
---

# Close Planner after a failed load

## Trigger

The initial load failed and the user closes Planner.

## Outcome

Planner is hidden and any reserved sidebar space is released; nothing in the graph changes.

## Edge cases

- Escape first cancels an active date drag, then closes a menu, then a narrow panel drawer; closing Planner is the final action.
