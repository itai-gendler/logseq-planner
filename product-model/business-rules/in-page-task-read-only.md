---
appliesTo:
- type: entity
  id: task
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

# In-page views never change task facts

In-page views present saved results and open items or Planner. Date and choice edits occur in the interactive Planner surface.
