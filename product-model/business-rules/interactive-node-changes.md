---
appliesTo:
- type: entity
  id: node
  effect: changes
  facts:
  - Dates
  - Choices
  contexts:
  - place: planner
permits:
- actors:
  - planner-user
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
---

# Planner users change node dates and choices in Planner

The interactive planning surface lets the person using the open graph move nodes between choice values and dates. Logseq supplies graph access and persistence. Dragging or resizing a span directly also needs Edit dates.
