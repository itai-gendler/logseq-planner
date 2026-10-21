---
appliesTo:
- type: entity
  id: saved-view
  facts:
  - Name
- type: entity
  id: planner-view-block
  facts:
  - Saved view name
references:
- kind: code
  role: implementation
  target: src/storage.ts#sanitizeViewName
- kind: code
  role: implementation
  target: src/ui/block.ts#findView
- kind: doc
  role: intent
  target: docs/guide.md
---

# Saved-view names are normalized before creation

The name drops #, square brackets and braces, folds runs of each parenthesis to one, and collapses surrounding and repeated whitespace. The resulting name must be nonempty. An in-page lookup tries the exact name first and then ignores case, taking the first match in saved page order.
