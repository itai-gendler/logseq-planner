---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Set Filters, Find or Added in Planner state
  kind: actor
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Filters
    - Find
    - Added
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Read Node and Task facts to present the matching work
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
  - entity: planner-state
    effect: changes
    facts:
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
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

# Narrow work by values, title and creation day

## Trigger

The user narrows a planning view.

## Outcome

Matching nodes and matching linked work are shown; progress and derived spans still use all linked tasks.

## Edge cases

- Choice properties combine with AND; selected values within a property combine with OR; no selection means unrestricted.
- No value matches an absent choice. Find requires every word, ignoring case, in the resolved title.
- Added is creation day, not last modification; Last N days includes today and N−1 prior days.
- If a node does not match but a linked task does, retain the node and only its matching task rows.
- Clear all removes choice and Tag filters, Added and Find together.
