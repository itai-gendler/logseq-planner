---
kind: alternate
routes:
  main: Planner in Logseq
steps:
- text: The host changes the current graph
  entities: []
  kind: condition
  contexts:
    main:
      place: planner::planning-view
  unattended: true
- text: Reset Planner state for the newly opened graph
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Saved view
    - Displayed data
    - Anchor day
    - Expanded task rows
    - Collapsed parents
    - Open Agenda buckets
    - Error
  kind: product
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

# Load the newly opened graph

## Trigger

Logseq switches the current graph in the same session.

## Outcome

The old view data, remembered per-kind settings and page-renderer registrations are cleared; the new graph’s saved preferences and default behavior apply when shown.

## Edge cases

- Hidden Planner waits until shown to load.
- An unused graph starts with defaults.
- The new graph’s remembered device surface is restored when available.
