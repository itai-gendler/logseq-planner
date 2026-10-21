---
references:
- kind: code
  role: implementation
  target: src/storage.ts
- kind: doc
  role: intent
  target: docs/guide.md
---

# Saved views

The Saved views section of Planner: named planning configurations kept in the graph.

## Boundary

Owns saving, updating, listing, opening and deleting saved views. Does not own showing a saved view in a page, which belongs to the in-page Planner view, nor general page editing, which stays with Logseq.
