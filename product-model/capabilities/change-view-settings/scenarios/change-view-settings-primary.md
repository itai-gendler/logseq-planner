---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose the date mapping, dependency property or done values
  kind: actor
  entities:
  - entity: property
    effect: reads
    facts:
    - Title
    - Type
    - Closed values
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the selected interpretation to every view.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Include child tags
    - Date mappings
    - Depends on
    - Done values
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#renderSettings
- kind: code
  role: implementation
  target: src/core/view-config.ts#defaultDates
- kind: code
  role: implementation
  target: src/core/nodes.ts#isDone
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change view settings

## Trigger

The current tag interpretation needs changing.

## Outcome

Planner state applies the selected interpretation to every view.

## Edge cases

- Start and End defaults prefer Start/End, then Scheduled/Deadline, then the first date property.
- Depends on defaults to a node property whose normalized title is dependson; None stops dependency exclusion.
- An explicit empty Done when selection closes no nodes for that property.
