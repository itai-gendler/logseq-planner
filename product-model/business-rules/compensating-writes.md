---
appliesTo:
- type: capability
  id: move-card
- type: capability
  id: move-dated-item
- type: capability
  id: resize-dated-item
references:
- kind: code
  role: implementation
  target: src/core/write.ts#writeInOrder
- kind: code
  role: implementation
  target: src/ui/workspace.ts#moveWhen
- kind: doc
  role: intent
  target: docs/guide.md
---

# A failed later move write attempts to restore earlier confirmed values

A multi-property move is written in order. Failure triggers restoration in reverse order, with read-back checks; the error distinguishes successful restoration from a restoration failure. A combined date and choice move restores dates if its later choice write fails. The result shown is what the graph holds.
