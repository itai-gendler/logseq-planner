---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose Agenda settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the Agenda settings. Date groups deduplicate linked tasks; Node groups retain them
    for each node. Show done applies the Agenda horizon.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Agenda settings
    - Displayed data
  - entity: node
    effect: reads
    facts:
    - Progress
  - entity: task
    effect: reads
    facts:
    - References
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/agenda.ts#layoutAgenda
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change Agenda settings

## Trigger

The user adjusts the Agenda view.

## Outcome

Planner state applies the Agenda settings. Date groups deduplicate linked tasks; Node groups retain them for each node. Show done applies the Agenda horizon.
