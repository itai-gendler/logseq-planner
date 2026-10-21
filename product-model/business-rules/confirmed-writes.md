---
appliesTo:
- type: capability
  id: save-saved-view
- type: capability
  id: update-saved-view
- type: capability
  id: delete-saved-view
- type: capability
  id: move-card
- type: capability
  id: move-dated-item
- type: capability
  id: resize-dated-item
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
- kind: code
  role: implementation
  target: src/core/kanban.ts#writeOne
- kind: code
  role: implementation
  target: src/core/date-edit.ts#writeDates
- kind: doc
  role: intent
  target: docs/guide.md
---

# A planning write succeeds only after its graph value is read back

Saved configurations, choice moves and date writes are checked against the graph. Pending changes are displayed optimistically; success and failure both reload the actual graph values. Saving a new view also checks its stored name, and deleting checks the block is absent.
