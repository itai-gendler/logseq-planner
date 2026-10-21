---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Close panel
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Panel to closed for the current width context.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Panel
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

# Hide the panel

## Trigger

The user hides the tag and filter panel.

## Outcome

The view takes the full width while ticked filters keep applying; a badge counts the ticked values.
