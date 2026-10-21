---
appliesTo:
- type: entity
  id: node
  facts:
  - Dates
- type: entity
  id: task
  facts:
  - Scheduled
  - Deadline
references:
- kind: code
  role: implementation
  target: src/core/date-edit.ts#shiftDate
- kind: code
  role: implementation
  target: src/core/date-edit.ts#writeDates
- kind: code
  role: implementation
  target: src/core/normalize.ts#buildNodes
- kind: doc
  role: intent
  target: docs/guide.md
---

# Date moves preserve local calendar meaning

DateTime moves by whole days retain local wall-clock time across timezone offset changes. A new undated DateTime starts at midnight. A Date write refers to the target day’s journal page, creating that page through Logseq when needed. A date with no journal day means no date.
