---
appliesTo:
- type: entity
  id: node
  facts:
  - References
  - Progress
- type: capability
  id: browse-planning-view
references:
- kind: code
  role: implementation
  target: src/core/layout-common.ts#nestItems
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Nested nodes have at most one level of parentage

A non-dependency reference can make a node a child. Candidate parents are considered in start, end, title order, with undated nodes last. A parent cannot also be a child; a grandchild stays top level. In a two-node reference cycle the later node becomes the child. Calendar, Kanban and Matrix do not nest.
