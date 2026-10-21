---
kind: alternate
routes:
  main: Agenda in a Logseq page
steps:
- text: Close a section in the Planner view block
  kind: actor
  actor: planner-user
  entities:
  - entity: planner-view-block
    effect: reads
    facts:
    - Result
    - Open Agenda buckets
  contexts:
    main:
      place: in-page::planner-view
- text: Change the Planner view block’s locally open sections
  kind: product
  actor: planner-user
  entities:
  - entity: planner-view-block
    effect: changes
    facts:
    - Open Agenda buckets
  contexts:
    main:
      place: in-page::planner-view
references:
- kind: code
  role: implementation
  target: src/ui/block.ts#readOnly
- kind: code
  role: implementation
  target: src/ui/view-area.ts#blockSession
---

# Close an in-page Agenda section

## Trigger

The user closes an expanded Agenda section in a page.

## Outcome

The entries are folded locally; graph content and the saved configuration stay unchanged.
