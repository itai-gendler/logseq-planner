---
kind: validation
routes:
  main: Planner in Logseq
steps:
- text: Inspect the sole selected Tag
  entities:
  - entity: tag
    effect: reads
    facts:
    - Title
  kind: actor
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
- text: Keep Planner state unchanged because its selection is already minimal
  entities:
  - entity: planner-state
    effect: reads
    facts:
    - Selected tags
  kind: product
  contexts:
    main:
      place: planner::planning-view
  actor: planner-user
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#tickTag
- kind: code
  role: implementation
  target: src/core/view-config.ts#withTags
- kind: doc
  role: intent
  target: docs/guide.md
---

# Retain the last selected tag

## Trigger

One tag remains selected.

## Outcome

The view retains that tag and its data.
