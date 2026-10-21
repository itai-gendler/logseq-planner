---
appliesTo:
- type: capability
  id: move-dated-item
- type: capability
  id: resize-dated-item
- type: entity
  id: planner-state
  facts:
  - Edit dates
references:
- kind: code
  role: implementation
  target: src/core/timeline-layout.ts#spanEdit
- kind: code
  role: implementation
  target: src/core/calendar-layout.ts#layoutGrid
- kind: code
  role: implementation
  target: src/ui/workspace.ts#gridEdit
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Direct span editing follows Edit dates and the span’s editable dates

Timeline and Calendar time-grid direct moves and resizes operate when Edit dates is enabled. They change the node’s own mapped dates; derived spans and linked task markers remain fixed. Timeline Day requires DateTime values; Calendar time grids edit same-day DateTime spans or points. A point moves only. Calendar day drops and Agenda/When rescheduling remain separate day-based actions.
