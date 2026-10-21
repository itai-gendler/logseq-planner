---
appliesTo:
- type: capability
  id: browse-planning-view
- type: capability
  id: move-card
- type: capability
  id: move-dated-item
references:
- kind: code
  role: implementation
  target: src/core/when.ts#whenPeriods
- kind: doc
  role: intent
  target: docs/guide.md
---

# When periods are successive non-overlapping date ranges

Overdue, Today, Tomorrow, This week, Next week, This month, This quarter and Later partition dated work in that order; periods with no remaining days are omitted. Weeks use Logseq’s week start. No date is separate. Overdue and Later have no writable target day.
