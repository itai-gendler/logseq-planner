---
kind: primary
routes:
  main: Planner in Logseq
steps:
- text: Choose Calendar settings
  kind: actor
  entities: []
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
- text: Planner state applies the Calendar settings. The period follows the chosen layout and Logseq week start;
    navigation shifts one month, seven days, three days or one day respectively.
  kind: product
  entities:
  - entity: planner-state
    effect: changes
    facts:
    - Calendar settings
    - Displayed data
  actor: planner-user
  contexts:
    main:
      place: planner::planning-view
references:
- kind: code
  role: implementation
  target: src/core/calendar-layout.ts#calendarRange
- kind: doc
  role: intent
  target: docs/guide.md
---

# Change Calendar settings

## Trigger

The user adjusts the Calendar view.

## Outcome

Planner state applies the Calendar settings. The period follows the chosen layout and Logseq week start; navigation shifts one month, seven days, three days or one day respectively.
