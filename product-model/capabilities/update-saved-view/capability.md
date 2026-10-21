---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
- kind: code
  role: implementation
  target: src/ui/workspace.ts#viewsWrite
- kind: doc
  role: intent
  target: docs/guide.md
domain: saved-views
---

# Update saved view

Replace the active saved view’s settings with the current settings, preserving its name.
