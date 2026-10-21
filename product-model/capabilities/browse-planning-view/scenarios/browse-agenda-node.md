---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the Agenda grouped by node
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Present each node’s progress and linked work, newest groups first, then groups with overdue work, then by date.
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
  target: src/core/agenda.ts
---

# Read the Agenda by node

## Trigger

The user opens the Agenda grouped by node.

## Outcome

Each node is a group with its progress and its linked work. Groups are ordered newest first, then groups with overdue work, then by their earliest date.

## Edge cases

- A group is as new as its newest node or task.
- A shared task appears under each node, once within a nested parent group.
- Multi-tag nesting follows the same parent selection as Timeline.
