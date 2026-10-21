---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Select the Tag
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
- text: Planner state selects that tag alone, resets its view settings and filters, and detaches the saved configuration
    association.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Include child tags
    - Date mappings
    - Depends on
    - Done values
    - Filters
    - Find
    - Added
    - Timeline settings
    - Calendar settings
    - Agenda settings
    - Kanban settings
    - Matrix settings
    - Saved view
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
  target: src/ui/workspace.ts#selectTag
- kind: code
  role: implementation
  target: src/core/view-config.ts#defaultViewConfig
- kind: doc
  role: intent
  target: docs/guide.md
---

# Select tag

## Trigger

The user chooses a tag name.

## Outcome

Planner state selects that tag alone, resets its view settings and filters, and detaches the active saved view.
