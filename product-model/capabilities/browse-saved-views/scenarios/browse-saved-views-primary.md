---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Browse Saved view entries
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
    - Readability
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Load Saved view settings from the graph
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Settings
    - Readability
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
- kind: code
  role: implementation
  target: src/ui/workspace.ts#listViews
- kind: doc
  role: intent
  target: docs/guide.md
---

# List saved configurations

## Trigger

The user opens Saved views.

## Outcome

All listed saved configurations can be identified; unreadable entries retain their deletion action.

## Edge cases

- A missing views page is an empty list.
- One malformed configuration does not hide other saved views.
- Reopening Planner reloads the list so external additions and deletions can appear.
