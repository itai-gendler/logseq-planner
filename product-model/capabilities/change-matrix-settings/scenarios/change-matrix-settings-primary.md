---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose Matrix settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the Matrix settings. Choosing the other axis swaps axes. Reverse and the split determine
    band membership; blank labels use the matching preset or band values. Hidden values are retained per property.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Matrix settings
    - Displayed data
  - entity: property
    effect: reads
    facts:
    - Title
    - Closed values
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#withAxis
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change Matrix settings

## Trigger

The user adjusts the Matrix view.

## Outcome

Planner state applies the Matrix settings. Choosing the other axis swaps axes. Reverse and the split determine band membership; blank labels use the matching preset or band values. Hidden values are retained per property.
