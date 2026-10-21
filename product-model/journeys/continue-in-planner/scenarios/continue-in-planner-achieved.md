---
kind: primary
result: achieved
routes:
  main: From a Logseq page
steps:
- text: Open the Saved view in Planner
  kind: actor
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Name
  capability: open-saved-view
  actor: planner-user
  contexts:
    main:
      place: in-page::planner-view
- text: Apply the Saved view to Planner state in the workspace
  kind: product
  entities:
  - entity: saved-view
    effect: reads
    facts:
    - Settings
  - entity: planner-state
    effect: changes
    facts:
    - Surface
    - Saved view
    - Displayed data
  capability: open-saved-view
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Browse the Node and Task results
  kind: actor
  entities:
  - entity: node
    effect: reads
    facts:
    - Title
    - Span
    - Progress
  - entity: task
    effect: reads
    facts:
    - Title
    - Scheduled
    - Deadline
  capability: browse-planning-view
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
---

# Continue from the page into Planner

## Trigger

The user chooses Open in Planner on a saved view in a Logseq page.

## Outcome

The same saved configuration is available for interactive browsing in the workspace, including when Planner previously used the sidebar.
