---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Enter focus
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Focus to on.
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

# Focus on the view

## Trigger

The user chooses Focus.

## Outcome

The header and controls are hidden; one line names the current view and brings the controls back.
