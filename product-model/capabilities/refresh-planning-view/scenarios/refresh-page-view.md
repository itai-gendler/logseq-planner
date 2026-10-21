---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: A graph change or visible periodic check requires fresh data
  kind: condition
  entities: []
  unattended: true
  contexts:
    main:
      place: in-page::planner-view
- text: Read current Node and Task facts
  kind: product
  entities:
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
  contexts:
    main:
      place: in-page::planner-view
- text: Refresh the Planner view block result
  kind: product
  entities:
  - entity: planner-view-block
    effect: changes
    facts:
    - Result
  contexts:
    main:
      place: in-page::planner-view
references:
- kind: code
  role: implementation
  target: src/ui/changes.ts#createChanges
- kind: code
  role: implementation
  target: src/ui/workspace.ts#reload
- kind: code
  role: implementation
  target: src/ui/block.ts#createBlocks
- kind: doc
  role: intent
  target: docs/guide.md
---

# Refresh a view in a page

## Trigger

The graph changes or a periodic check observes new data.

## Outcome

The displayed result reflects the graph; unchanged data need not redraw.

## Edge cases

- Multiple blocks naming the same saved view share its load during a refresh pass.
- A removed or unreadable saved view is replaced by an explanatory message.
