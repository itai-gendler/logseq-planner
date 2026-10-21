---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
- kind: code
  role: implementation
  target: src/ui/workspace.ts#listViews
- kind: doc
  role: intent
  target: docs/guide.md
- kind: code
  role: implementation
  target: src/core/view-config.ts#parseViewConfig
- kind: code
  role: implementation
  target: src/sdk.ts#storageDeps
- kind: doc
  role: intent
  target: docs/plugin-config.md
domain: saved-views
---

# Browse saved views

List the graph's saved views in page order, each to open or delete, including one whose settings cannot be read, with the reason.

Views kept on the older Planner views page stay readable, and the page is renamed when possible. Older single-tag views and settings added in later releases get their supported defaults.
