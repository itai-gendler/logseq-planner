---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open Planner
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Load Planner state for this graph
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts: []
    from: Hidden
    to: Loading
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Restore Planner state and present the graph
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Selected tags
    - Include child tags
    - Date mappings
    - Depends on
    - Done values
    - Filters
    - Find
    - Added
    - View kind
    - Timeline settings
    - Calendar settings
    - Agenda settings
    - Kanban settings
    - Matrix settings
    - Saved view
    - Anchor day
    - Expanded task rows
    - Collapsed parents
    - Open Agenda buckets
    - Panel
    - Focus
    - Surface
    - Edit dates
    - Error
    - Displayed data
    - Title width
    - Dock width
    from: Loading
    to: Ready
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openBody
- kind: code
  role: implementation
  target: src/ui/workspace.ts#initialTag
- kind: code
  role: implementation
  target: src/ui-state.ts#createUiStore
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open the remembered planning context

## Trigger

The user opens Planner from Logseq.

## Outcome

Planner is ready with the graph’s remembered settings; the graph copy of the current view and title width wins over the device copy.

## Edge cases

- Unreadable remembered settings use the default view without an error.
- A graph with no tags shows its empty state.
- Panel, surface, folded headings and Edit dates are device preferences; the period and expanded rows start afresh.
