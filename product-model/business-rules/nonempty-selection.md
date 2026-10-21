---
appliesTo:
- type: entity
  id: planner-state
  facts:
  - Selected tags
references:
- kind: code
  role: implementation
  target: src/ui/workspace.ts#tickTag
- kind: code
  role: implementation
  target: src/core/view-config.ts#withTags
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# A planning view retains at least one selected tag

The last tag cannot be removed. Adding or removing a tag retains date mappings for surviving tags and discards settings that no longer apply.
