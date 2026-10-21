---
appliesTo:
- type: entity
  id: planner-state
references:
- kind: code
  role: implementation
  target: src/ui-state.ts#createUiStore
- kind: code
  role: implementation
  target: src/ui/workspace.ts#restorePrefs
- kind: doc
  role: intent
  target: docs/guide.md
---

# The graph’s remembered view wins over the device copy on open

The current view and Timeline title width follow the graph. Panel state, folded headings, surface and Edit dates remain device preferences per graph; dock width is a device preference. The session period, expanded rows and open menus are not restored. Unreadable stored state falls back to defaults or the readable device copy, and persistence is best effort.
