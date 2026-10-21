---
appliesTo:
- type: capability
  id: refresh-planning-view
- type: entity
  id: planner-state
  facts:
  - Displayed data
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

# Refresh preserves the current reading context and waits for active interactions

Graph changes are coalesced and visible results are checked periodically. Refresh waits during a menu, drag or write, retains scroll, expanded rows, open buckets and focus, and redraws only when presented data changes. Hidden Planner remembers stale data until shown; in-page blocks continue independently.
