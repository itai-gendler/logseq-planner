---
appliesTo:
- type: entity
  id: planner-state
  facts:
  - Filters
  - Find
  - Added
- type: entity
  id: node
  facts:
  - Span
  - Progress
references:
- kind: code
  role: implementation
  target: src/core/narrow.ts#narrowItems
- kind: code
  role: implementation
  target: src/ui/view-area.ts#itemsOf
- kind: doc
  role: intent
  target: docs/guide.md
---

# Find and Added do not reduce progress or derived spans

Find matches every word in a resolved title without case sensitivity. Added uses local creation days and not modification time. A matching node retains all its tasks; otherwise matching tasks retain the node and only their own rows. Span and progress still use all linked tasks. Choice filters apply before this narrowing.
