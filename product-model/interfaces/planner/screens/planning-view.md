---
entities:
- entity: planner-state
  shows:
  - Selected tags
  - Include child tags
  - Date mappings
  - Depends on
  - Done values
  - Filters
  - Find
  - Added
  - View kind
  - Timeline settings
  - Calendar settings
  - Agenda settings
  - Kanban settings
  - Matrix settings
  - Saved view
  - Anchor day
  - Expanded task rows
  - Collapsed parents
  - Open Agenda buckets
  - Panel
  - Focus
  - Surface
  - Edit dates
  - Error
  - Displayed data
  - Title width
  - Dock width
  collects:
  - Selected tags
  - Include child tags
  - Date mappings
  - Depends on
  - Done values
  - Filters
  - Find
  - Added
  - View kind
  - Timeline settings
  - Calendar settings
  - Agenda settings
  - Kanban settings
  - Matrix settings
  - Saved view
  - Anchor day
  - Expanded task rows
  - Collapsed parents
  - Open Agenda buckets
  - Panel
  - Focus
  - Surface
  - Edit dates
  - Title width
  - Dock width
- entity: saved-view
  shows:
  - Name
  - Settings
  - Readability
  collects:
  - Name
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
- entity: tag
  shows:
  - Title
  - Built in
  - Parents
  - Properties
- entity: property
  shows:
  - Title
  - Type
  - Closed values
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#renderWorkspace
---

# Planning view

One working context for the selected planning subject. Timeline, Calendar, Agenda, Kanban and Matrix present the same selected work; settings and saved-view selection remain part of this context.
