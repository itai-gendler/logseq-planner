---
appliesTo:
- type: entity
  id: task
  effect: changes
  facts:
  - Scheduled
  - Deadline
  contexts:
  - place: planner
permits:
- actors:
  - planner-user
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#createWorkspace
---

# Planner users reschedule linked tasks in Planner

The interactive planning surface lets the person using the open graph move a linked task's Scheduled and Deadline by day or When period, in the Calendar and the Agenda. Logseq supplies graph access and persistence.
