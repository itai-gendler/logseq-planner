---
references:
- kind: code
  role: implementation
  target: src/ui/timeline.ts
- kind: doc
  role: intent
  target: docs/guide.md
---

# Timeline

The Timeline section of Planner: nodes as rows of bars and points over a day, week, month or quarter.

## Boundary

Owns the Timeline's Zoom and Arrange settings and folding of task rows and nested parents. Does not own date moves or browsing, which every dated view shares.
