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

# Close Agenda bucket

Fold the Agenda's Later, No date or Earlier bucket again, so its entries are no longer listed. In a page, a reader folds an in-page Agenda's bucket locally; this changes neither the graph nor the saved view.
