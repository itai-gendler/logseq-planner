---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/core/date-edit.ts#dateChanges
- kind: code
  role: implementation
  target: src/core/timeline-layout.ts#clampDelta
- kind: code
  role: implementation
  target: src/core/calendar-layout.ts#gridDelta
- kind: doc
  role: intent
  target: docs/guide.md
---

# Resize dated item

Change one end of an eligible node’s existing span with Edit dates enabled in Timeline or Calendar time grids.
