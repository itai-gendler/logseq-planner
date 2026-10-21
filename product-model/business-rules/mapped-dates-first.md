---
appliesTo:
- type: entity
  id: node
  facts:
  - Dates
  - Span
- type: entity
  id: task
  facts:
  - Scheduled
  - Deadline
references:
- kind: code
  role: implementation
  target: src/core/nodes.ts#resolveSpan
- kind: doc
  role: intent
  target: docs/guide.md
---

# A node’s own mapped dates take precedence over linked task dates

Both own values define a span; one defines a point. With neither, the earliest to latest Scheduled or Deadline among linked tasks supplies a derived span, regardless of task status. Without any date the node is undated.
