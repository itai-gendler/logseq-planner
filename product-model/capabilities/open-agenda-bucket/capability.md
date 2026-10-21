---
availability:
- place: planner
- place: in-page
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: code
  role: implementation
  target: src/ui/block.ts#readOnly
- kind: doc
  role: intent
  target: docs/guide.md
domain: agenda
---

# Open Agenda bucket

Unfold the Agenda's Later, No date or Earlier bucket to list its entries; these buckets start folded. In a page, a reader unfolds an in-page Agenda's bucket locally; this changes neither the graph nor the saved view.
