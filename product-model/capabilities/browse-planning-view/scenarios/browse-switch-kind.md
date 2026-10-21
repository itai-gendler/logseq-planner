---
kind: alternate
routes:
  main: Planner in Logseq
steps:
- text: Choose another view kind
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Change Planner state View kind and restore its applicable settings
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - View kind
    - Timeline settings
    - Calendar settings
    - Agenda settings
    - Kanban settings
    - Matrix settings
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

# Return to a view kind in the same session

## Trigger

The user changes view kind.

## Outcome

Shared interpretation stays current; this kind’s last settings return only for the same ordered tags and only while valid.

## Edge cases

- A missing remembered configuration or an invalid property uses that kind’s defaults.
- Changing kind does not change the session anchor day.
