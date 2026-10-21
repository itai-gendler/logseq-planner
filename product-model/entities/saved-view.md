---
references:
- kind: code
  role: implementation
  target: src/storage.ts#createViewStore
relations:
- entity: planner-view-block
  verb: is named by
  cardinality: one-to-many
---

# Saved view

A named, graph-backed planning configuration reused in Planner and in pages. Each saved view has its own block on Plugin views: Planner.

## Information kept

- **Name** — The name shown in the saved-view list and used by in-page views.
- **Settings** — Tags, mappings, filtering and view-specific settings captured when saved or updated, excluding the current period and device preferences.
- **Readability** — Readable settings or the reason stored settings cannot be read.
