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
      place: planner::planning-view
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
      place: planner::planning-view
- text: Refresh Planner state while preserving the current reading position
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Displayed data
  contexts:
    main:
      place: planner::planning-view
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

# Refresh the visible view

## Trigger

The graph changes or a periodic check observes new data.

## Outcome

The displayed result reflects the graph; unchanged data need not redraw.

## Edge cases

- The interactive surface waits while a menu, drag or write is active.
- Hidden interactive Planner records staleness and reloads on the next show; in-page views have their own refresh cycle.
- Visible periodic checks run every 30 seconds; this does not promise a sync delivery time.
