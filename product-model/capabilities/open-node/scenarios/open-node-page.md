---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Open the Node or Task
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  - entity: task
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
- text: Ask Logseq to open the selected Node or Task
  kind: product
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
  - entity: task
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
references:
- kind: code
  role: implementation
  target: src/app.ts#nodeOpener
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open an item from a page

## Trigger

The user clicks a node or linked task in a Planner view in a page.

## Outcome

Logseq opens the selected page or block.

## Edge cases

- A Planner view in a page opens items in the main page only.
