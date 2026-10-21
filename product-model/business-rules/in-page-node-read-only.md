---
appliesTo:
- type: entity
  id: node
  effect: changes
  contexts:
  - place: in-page
references:
- kind: code
  role: implementation
  target: src/ui/block.ts#readOnly
- kind: doc
  role: intent
  target: docs/guide.md
permits: []
---

# In-page views never change node facts

In-page views present saved results and open items or Planner. Date and choice edits occur in the interactive Planner surface.
