---
appliesTo:
- type: entity
  id: property
  effect: creates
references:
- kind: code
  role: implementation
  target: src/core/schema.ts#buildTagInfos
- kind: spec
  role: intent
  target: REQUIREMENTS.md
permits: []
---

# Planner never creates user tag properties

Planning uses the properties already offered by the user’s tags. Plugin-owned configuration properties are not user tag properties.
