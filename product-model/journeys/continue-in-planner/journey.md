---
actors:
- planner-user
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openView
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: doc
  role: intent
  target: docs/guide.md
---

# Continue in Planner

## Goal

Continue examining the same saved planning view from a Logseq page in the interactive workspace.

## Success criterion

Planner opens the named saved configuration in the workspace and the user can inspect its work there.
