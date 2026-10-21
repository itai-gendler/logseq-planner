---
references:
- kind: code
  role: implementation
  target: src/ui/block.ts#createBlocks
---

# Planner view block

A block in a Logseq page that names a saved view and presents its current read-only result.

## Information kept

- **Saved view name** — The requested saved-view name, including names containing commas.
- **Result** — The rendered planning result or a message explaining why it cannot be shown.
- **Open Agenda buckets** — Later, No date or Earlier sections expanded locally in this page rendering.
