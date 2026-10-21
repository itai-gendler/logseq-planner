---
appliesTo:
- type: entity
  id: saved-view
  facts:
  - Settings
- type: entity
  id: planner-state
  facts:
  - Anchor day
  - Saved view
references:
- kind: code
  role: implementation
  target: src/core/view-config.ts#serializeViewConfig
- kind: code
  role: implementation
  target: src/ui/workspace.ts#openSaved
- kind: doc
  role: intent
  target: docs/guide.md
---

# A saved view stores interpretation and layout choices, not the current period

Saved settings include ordered tags, child inclusion, per-tag dates, dependencies, Done when, filters, Find, Added and view-specific choices. Opening applies the saved settings; Update replaces the stored copy under its existing name. The relative Added window is evaluated against the day the view is read.
