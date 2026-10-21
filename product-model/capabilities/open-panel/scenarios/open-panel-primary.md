---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open panel
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Panel to open for the current width context.
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

# Show the panel

## Trigger

The user shows the panel again.

## Outcome

The tag tree, Find, Added and filters are available; in narrow Planner the panel opens as a drawer over the view.
