---
kind: primary
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
    from: Ready
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

# Close Planner

## Trigger

The user closes Planner with Close, Escape or the toolbar button.

## Outcome

Planner is hidden, any reserved sidebar space is released, and the next open in this graph returns to the same view and surface.

## Edge cases

- Escape first cancels an active date drag, then closes a menu, then a narrow panel drawer; closing Planner is the final action.
