---
appliesTo:
- type: entity
  id: property
- type: entity
  id: tag
references:
- kind: code
  role: implementation
  target: src/core/schema.ts#collectProps
- kind: code
  role: implementation
  target: src/core/schema.ts#mergeTags
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Choice controls use properties shared by every selected tag

Properties match by graph identity, never title. Filters, Done when, Kanban choices and Priority use the shared single-valued choice properties. Depends on uses the union of node-reference properties. Own and inherited properties contribute; many-valued choices are not choice controls.
