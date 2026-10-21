---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Timeline
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present dated nodes by start, their spans and progress, points, linked task dates, dependency relations,
    undated nodes and counts of earlier or later nodes.
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
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/timeline-layout.ts
---

# Read the Timeline

## Trigger

The user opens the Timeline.

## Outcome

Each dated node in the period is a row with its span or point and progress, linked task dates are marked, dependencies are drawn as arrows, and undated nodes are listed apart.

## Edge cases

- Only nodes touching the period have rows; earlier and later counts lead to the nearest such dates.
- Nested parents without a visible row leave their children at top level.
