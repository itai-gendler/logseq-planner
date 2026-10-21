---
entities:
- entity: saved-view
  shows:
  - Name
  - Settings
  - Readability
- entity: node
  shows:
  - Title
  - Tags
  - Dates
  - Choices
  - Fields
  - References
  - Span
  - Progress
- entity: task
  shows:
  - Title
  - Scheduled
  - Deadline
  - Status
  - References
- entity: planner-view-block
  shows:
  - Saved view name
  - Result
  - Open Agenda buckets
  collects:
  - Saved view name
references:
- kind: code
  role: implementation
  target: src/ui/block.ts#viewBlock
---

# Planner view in a page

A named saved view within the current page, including its result and any loading message.
