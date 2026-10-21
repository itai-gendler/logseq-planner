---
type: web
actors:
- planner-user
references:
- kind: code
  role: implementation
  target: src/app.ts#registerApp
- kind: doc
  role: intent
  target: README.md
---

# Planner

The interactive Planner surface inside Logseq, used as a workspace or docked beside the page on desktop. Its toolbar, palette command and non-editing shortcut enter the same product context. The embedded web surface works in Logseq desktop and web; desktop-only behavior is named where it applies.
