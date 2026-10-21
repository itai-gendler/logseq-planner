---
appliesTo:
- type: entity
  id: planner-state
  facts:
  - Kanban settings
  - Matrix settings
- type: capability
  id: move-card
references:
- kind: code
  role: implementation
  target: src/core/kanban.ts#layoutKanban
- kind: code
  role: implementation
  target: src/core/matrix.ts#axisBands
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: doc
  role: intent
  target: docs/guide.md
---

# At least one column or axis value stays shown

Kanban Show keeps at least one column. Matrix Every value keeps at least one value per axis. Stored hidden lists that hide every available value show all instead. Hidden values leave the result with their cards, not the graph; Kanban Move still includes hidden columns.
