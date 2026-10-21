---
references:
- kind: code
  role: implementation
  target: src/core/normalize.ts#buildTasks
- kind: code
  role: implementation
  target: src/core/layout-common.ts#taskState
---

# Task

A #Task block linked to a selected node by reference. It retains its own identity, dates and status; when selected as a node it is not repeated as a linked-task row.

## Information kept

- **Title** — The displayed task title.
- **Scheduled** — Its Scheduled date and time, if present.
- **Deadline** — Its Deadline date and time, if present.
- **Status** — Its built-in status, including done and canceled meanings.
- **References** — The selected nodes it references, excluding references through Depends on.
- **Created day** — Its local creation day, when supplied by the graph.
