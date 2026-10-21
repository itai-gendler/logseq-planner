---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Add the Tag to the current selection
  kind: actor
  entities:
  - entity: tag
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state appends the tag in selection order, keeps existing mappings, adds defaults for the new tag
    and retains only compatible shared settings.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Date mappings
    - Depends on
    - Done values
    - Filters
    - Timeline settings
    - Kanban settings
    - Matrix settings
    - Displayed data
  - entity: tag
    effect: reads
    facts:
    - Title
    - Properties
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#tickTag
- kind: code
  role: implementation
  target: src/core/view-config.ts#withTags
- kind: doc
  role: intent
  target: docs/guide.md
---

# Add tag

## Trigger

The user adds a tag.

## Outcome

Planner state appends the tag in selection order, keeps existing mappings, adds defaults for the new tag and retains only compatible shared settings.

## Edge cases

- Crossing from one selected tag to several defaults Timeline arrangement to Nested.
- A lost Priority sort becomes Due; an unavailable lane becomes None.
