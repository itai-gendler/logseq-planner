---
appliesTo:
- type: entity
  id: planner-state
  facts:
  - Matrix settings
- type: capability
  id: move-card
references:
- kind: code
  role: implementation
  target: src/core/matrix.ts#axisBands
- kind: code
  role: implementation
  target: src/core/matrix.ts#matrixMove
- kind: doc
  role: intent
  target: docs/guide.md
---

# A Matrix move preserves values within unchanged bands

Each changed choice axis takes the first value in the target band’s order. Unplaced clears both axes, including dates when an axis is When. Band membership persists by value identity; new values join the second band and removed values are ignored. Every value exposes individual values rather than the two bands.
