---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Read the Planner view block
  kind: actor
  entities:
  - entity: planner-view-block
    effect: reads
    facts:
    - Saved view name
    - Result
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
- text: Resolve the Saved view by name and present Node and Task facts
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
    - Settings
    - Readability
  - entity: node
    effect: reads
    facts:
    - Title
    - Tags
    - Dates
    - Choices
    - Fields
    - References
    - Created day
    - Span
    - Progress
  - entity: task
    effect: reads
    facts:
    - Title
    - Scheduled
    - Deadline
    - Status
    - References
    - Created day
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
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

# Read a saved view in a page

## Trigger

A Planner view block is displayed in Logseq.

## Outcome

The saved configuration is shown anchored on today, without changing its graph items.

## Edge cases

- Exact name wins before case-insensitive matching; the first matching saved view in page order wins among duplicates.
- Nested children start open and task rows folded. Additional paged results are indicated as remaining counts.
- Unknown names list existing saved-view names or explain that a view must first be saved.
- Unreadable settings or unavailable schema show a message instead of a planning result.
