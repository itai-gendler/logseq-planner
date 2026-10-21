---
kind: validation
routes:
  main: Planner in Logseq
steps:
- text: Read the current planning result
  entities: []
  kind: actor
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
- text: Inspect Tag properties and Planner state to explain the empty result
  entities:
  - entity: tag
    effect: reads
    facts:
    - Properties
  - entity: planner-state
    effect: reads
    facts:
    - Selected tags
    - View kind
    - Displayed data
  kind: product
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
references:
- kind: code
  role: implementation
  target: src/ui/view-area.ts#renderViewArea
- kind: code
  role: implementation
  target: src/ui/workspace.ts#switchKind
- kind: code
  role: implementation
  target: src/core/narrow.ts#narrowItems
- kind: code
  role: implementation
  target: src/ui/block.ts#readOnly
- kind: doc
  role: intent
  target: docs/guide.md
---

# Explain missing planning data or mappings

## Trigger

The selected tags supply no nodes or lack the properties needed by this view.

## Outcome

Planner explains the missing data or schema and directs the user toward existing tags or property setup in Logseq.

## Edge cases

- A date view needs a selected tag with Date or DateTime properties.
- Kanban needs an available column property; Matrix needs two choice axes or a choice plus When.
- No matching nodes explains the filters and offers clearing them.
- The plugin never creates user tag properties to resolve the empty state.
