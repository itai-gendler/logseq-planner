---
availability:
- place: planner
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
- kind: code
  role: implementation
  target: src/core/fields.ts#cardFieldsOf
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change Kanban settings

Set Columns, Swimlanes, Show, Sort and Card fields.

Card fields offer the selected tag's own and inherited simple choice, date, text, number, checkbox, URL and node/page-reference properties. The column, swimlane, Priority and hidden properties are excluded. References display their titles, selected checkboxes display their names, and absent values are omitted. With no per-tag list, shared choice fields supply the default.
