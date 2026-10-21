---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Remove the Tag from the current selection
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
- text: Planner state removes the tag, its dates and incompatible settings; a single remaining tag has no Tag filter
    or Tag swimlane.
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

# Remove tag

## Trigger

At least two tags are selected.

## Outcome

Planner state removes the tag, its dates and incompatible settings; a single remaining tag has no Tag filter or Tag swimlane.

## Edge cases

- The last selected tag stays selected.
