---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/ui/view-area.ts#dateMoveOf
- kind: code
  role: implementation
  target: src/core/when.ts#whenMove
- kind: code
  role: implementation
  target: src/core/date-edit.ts#writeDates
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveDate
- kind: doc
  role: intent
  target: docs/guide.md
---

# Move dated item

Move a node or linked task to another day or When period from Calendar or Agenda, or move a node’s existing span in Timeline or a Calendar time grid. Existing durations and local times are retained.
