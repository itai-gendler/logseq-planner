---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose Timeline settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the Timeline settings. Day shows one day; Week 21 days; Month 56 days; Quarter 17
    weeks. By date, By tag and Nested share the same graph facts.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Timeline settings
    - Displayed data
  - entity: tag
    effect: reads
    facts:
    - Title
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/timeline-layout.ts#timelineRange
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change Timeline settings

## Trigger

The user adjusts the Timeline view.

## Outcome

Planner state applies the Timeline settings. Day shows one day; Week 21 days; Month 56 days; Quarter 17 weeks. By date, By tag and Nested share the same graph facts.
