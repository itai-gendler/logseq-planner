---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Leave focus
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Focus to off.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Focus
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

# Bring back the controls

## Trigger

The user leaves focus.

## Outcome

The header and controls of the current view are shown again.
