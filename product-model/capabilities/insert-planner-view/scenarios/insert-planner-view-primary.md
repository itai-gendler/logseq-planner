---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Invoke the page renderer and supply the saved configuration name
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
- text: Create the Planner view block in the host page
  kind: product
  entities:
  - entity: planner-view-block
    effect: creates
    facts:
    - Saved view name
    - Result
    - Open Agenda buckets
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
references:
- kind: code
  role: implementation
  target: src/app.ts#SLASH_COMMAND
- kind: code
  role: implementation
  target: src/ui/block.ts#macroViewName
- kind: doc
  role: intent
  target: docs/guide.md
---

# Place a saved view in a page

## Trigger

The user invokes Planner view while editing a Logseq block.

## Outcome

The page contains a named Planner renderer ready for Logseq to display.

## Edge cases

- The command inserts the renderer placeholder; the name is supplied in Logseq’s editor.
- Names containing commas are reconstructed from all name arguments.
