---
appliesTo:
- type: entity
  id: property
  effect: changes
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#renderSettings
- kind: spec
  role: intent
  target: REQUIREMENTS.md
permits: []
---

# Planner never changes user tag property definitions

Changing a view mapping selects an existing property; it does not change that property’s definition.
