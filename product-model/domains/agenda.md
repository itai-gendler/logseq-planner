---
references:
- kind: code
  role: implementation
  target: src/ui/agenda.ts
- kind: doc
  role: intent
  target: docs/guide.md
---

# Agenda

The Agenda section of Planner: what is overdue, due today and due in the next 14 days.

## Boundary

Owns the Agenda's grouping, Show done and its folded Later, No date and Earlier buckets. Does not own rescheduling, which the Agenda shares with the Calendar, Kanban and Matrix.
