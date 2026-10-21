---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose Kanban settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the Kanban settings. Columns use shared choices or When; Tag swimlanes need several
    selected tags. Card fields are selected per tag and hidden column choices are retained per property.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Kanban settings
    - Displayed data
  - entity: tag
    effect: reads
    facts:
    - Title
    - Properties
  - entity: property
    effect: reads
    facts:
    - Title
    - Closed values
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

# Change Kanban settings

## Trigger

The user adjusts the Kanban view.

## Outcome

Planner state applies the Kanban settings. Columns use shared choices or When; Tag swimlanes need several selected tags. Card fields are selected per tag and hidden column choices are retained per property.
