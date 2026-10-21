---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openBody
- kind: code
  role: implementation
  target: src/ui/workspace.ts#initialTag
- kind: code
  role: implementation
  target: src/ui-state.ts#createUiStore
- kind: doc
  role: intent
  target: docs/guide.md
---

# Open Planner

Open the current graph’s planning context from Logseq and restore its remembered view when readable. A fresh graph starts from the first own root tag with dates, then another own dated tag, then the first available tag.
