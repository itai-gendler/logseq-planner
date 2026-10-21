---
availability:
- place: planner
- place: in-page
references:
- kind: code
  role: implementation
  target: src/ui/changes.ts#createChanges
- kind: code
  role: implementation
  target: src/ui/workspace.ts#reload
- kind: code
  role: implementation
  target: src/ui/block.ts#createBlocks
- kind: doc
  role: intent
  target: docs/guide.md
---

# Refresh planning view

Reflect graph changes in the visible planning result, including changes made in another view or in Logseq. In-page views refresh independently of the interactive surface.
