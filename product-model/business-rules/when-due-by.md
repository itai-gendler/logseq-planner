---
appliesTo:
- type: capability
  id: move-card
- type: capability
  id: move-dated-item
- type: entity
  id: node
  facts:
  - Dates
references:
- kind: code
  role: implementation
  target: src/core/when.ts#whenMove
- kind: code
  role: implementation
  target: src/core/matrix.ts#axisBands
- kind: doc
  role: intent
  target: docs/guide.md
---

# A move by When writes the last day of its target period

An item already in the period keeps its date. Otherwise End lands on the last day and Start shifts equally; one own date moves alone. With no own date, End is preferred over Start. Clearing own dates can reveal a derived span again. A Matrix When band uses its last writable period; a band with only Overdue or Later cannot receive a move.
