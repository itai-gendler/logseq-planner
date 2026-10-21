---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Browse Tag names and find a matching title
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Title
    - Built in
    - Parents
    - Properties
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Read inherited Property definitions
  kind: product
  entities:
  - entity: property
    effect: reads
    facts:
    - Title
    - Type
    - Cardinality
    - Closed values
    - Hidden
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#renderTags
- kind: code
  role: implementation
  target: src/core/schema.ts#buildTagInfos
- kind: doc
  role: intent
  target: docs/guide.md
---

# Find a planning tag

## Trigger

The user wants a tag to plan.

## Outcome

The matching tags remain available for selection, with built-in and own tags distinguished.

## Edge cases

- Finding a tag changes the picker, not the nodes of the current view.
