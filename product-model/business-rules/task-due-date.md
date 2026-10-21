---
appliesTo:
- type: entity
  id: task
  facts:
  - Scheduled
  - Deadline
  - Status
- type: capability
  id: browse-planning-view
references:
- kind: code
  role: implementation
  target: src/core/layout-common.ts#dueDate
- kind: code
  role: implementation
  target: src/core/layout-common.ts#isLate
- kind: code
  role: implementation
  target: src/core/agenda.ts#layoutAgenda
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# A task’s Deadline takes precedence over Scheduled for lateness

An open task is late when its Deadline, otherwise Scheduled, is before today. Agenda files overdue tasks at that due date. Timeline marks that date, and Calendar Month presents linked deadlines rather than scheduled occurrences.
