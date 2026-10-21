---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open the Saved view
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
    - Settings
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
- text: Load the Saved view into Planner state
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Settings
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
    - Displayed data
    - Surface
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openSaved
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open a saved view from a page

## Trigger

The user chooses Open in Planner on a Planner view in a page.

## Outcome

Planner opens in the workspace on that saved view, even when it was last docked, keeping the period being looked at.

## Edge cases

- Missing selected tags are dropped while at least one remains.
- Settings that cannot be applied produce an explanatory error.
