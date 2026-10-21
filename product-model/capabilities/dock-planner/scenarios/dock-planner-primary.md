---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Dock Planner
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state sets Surface to Sidebar.
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

# Dock Planner beside the page

## Trigger

On the desktop app, the user docks Planner beside the current Logseq page.

## Outcome

Planner shows on the window's right edge with the same view, the page stays usable beside it, and the next open in this graph is docked too.
